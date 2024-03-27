
# Keeping SQLite Schema Diagram Up To Date

Recently, I read https://news.ycombinator.com/item?id=39798115 where a commenter said they have their CI run the SQLite diagram generator whenever changes are made to their migrations. 
I tried it out for my own project in this PR: https://github.com/lydavid/MusicSearch/pull/821. Though I decided to continue using SchemaCrawler because I wanted to see types as well.

## Run an Android emulator in GitHub Actions
https://github.com/ReactiveCircus/android-emulator-runner

Search for usages: https://github.com/search?q=reactivecircus%2Fandroid-emulator-runner+%22adb+pull%22&type=code
I searched for `adb pull` because I was looking for examples of extracting a database from an Android emulator. I wasn't able to find any, but I came across this, which served as stubbing for my workflow: https://github.com/beemdevelopment/Aegis/blob/master/.github/workflows/build-app-workflow.yaml

```yml
      - name: Tests
        uses: reactivecircus/android-emulator-runner@e790971012b979513b4e2fe70d4079bc0ca8a1ae
        with:
          api-level: 31
          arch: x86_64
          profile: pixel_3a
          heap-size: 512M
          ram-size: 4096M
          emulator-options: -memory 4096 -no-window -gpu swiftshader_indirect -noaudio -no-boot-anim -camera-back none
          disable-animations: true
          disk-size: 8G
          script: |
            mkdir -p artifacts/report
            adb logcat -c
            adb logcat -G 16M && adb logcat -g
            ./gradlew connectedCheck || touch tests_failing
            adb logcat -d > artifacts/logcat.txt
            cp -r app/build/reports/androidTests/connected/* artifacts/report/
            if adb shell '[ -e /sdcard/Pictures/screenshots ]'; then adb pull /sdcard/Pictures/screenshots artifacts/; fi
            test ! -f tests_failing
```

Another example, from Anki: https://github.com/ankidroid/Anki-Android/blob/main/.github/workflows/tests_emulator.yml

### Test locally
[Start emulator headless](til/emulator/start-emulator-emulator.md#Start%20emulator%20headless)
Then try running the same commands from `script`.

## Get the SQLite database from a running emulator using ADB
https://stackoverflow.com/a/36841916
```
adb shell "run-as io.github.lydavid.musicsearch.debug cat /data/data/io.github.lydavid.musicsearch.debug/databases/musicsearch.db" > musicsearch.db
```


## Use SchemaCrawler to generate an SVG from my database
https://github.com/schemacrawler/SchemaCrawler-Action

Example: https://github.com/schemacrawler/SchemaCrawler-Action-Usage-Example/actions/runs/7943155712
```yml
      - id: schemacrawler
        name: Run SchemaCrawler Action with specified command-line
        uses: schemacrawler/SchemaCrawler-Action@v16.21.2
        with:
          entrypoint: /schemacrawler.sh
          args: --server=sqlite --database=schemacrawler.sqlite --user:env USER --password:env PASSWORD --info-level=standard --command=brief --output-file database-diagram.png --log-level=CONFIG
        env:
          USER: user-possibly-from-secrets
          PASSWORD: password-possibly-from-secrets

      - id: upload-database-diagram
        name: Upload SchemaCrawler database diagram
        uses: actions/upload-artifact@v2
        with:
          name: database-diagram
          path: database-diagram.png
```


## Lessons learned

`./gradlew installDebug` installs my application, but does not start it, so `musicsearch.db` does not yet exist when I tried to extract it.

`adb shell am start -a android.intent.action.VIEW -d "io.github.lydavid.musicsearch.debug://app/history"` will launch my application, but this command must be run into the `script` block of `android-emulator-runner` otherwise the emulator would have shut down before it can run. Also, if I try to run another adb command afterwards, the application may still be starting up, so I had to `sleep`.

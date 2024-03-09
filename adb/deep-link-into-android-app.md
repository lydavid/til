
# Deep Link into Android App

The Android app would need to [support deep linking](https://developer.android.com/jetpack/compose/navigation#deeplinks). Then I can [execute adb shell](adb-shell-to-execute-commands.md) to start the app from an arbitrary screen with parameters[^1].

```shell
adb shell am start -a android.intent.action.VIEW -d '"io.github.lydavid.musicsearch.debug://app/lookup?query=tsukuyomi&type=artist"'
```

The above will open the MusicSearch app, and enter a search query for "tsukuyomi" under the artist resource.

Right now, I save a collection of deep links for testing purposes in a Markdown file: [https://github.com/lydavid/MusicSearch/blob/beta/docs/testing/deep_links.md](https://github.com/lydavid/MusicSearch/blob/beta/docs/testing/deep_links.md)

By adding `shell` to the code block, I can execute the adb command with Android Studio's gutter icon.

![](../attachments/Screenshot%202024-03-04%20230136.jpg)

[^1]: [https://developer.android.com/training/app-links/deep-linking#testing-filters](https://developer.android.com/training/app-links/deep-linking#testing-filters)
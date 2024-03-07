
# Charles Messes up Gradle Plugin/Dependency Downloads
In order to download these, I cannot use a proxy, so I will need to disable Charles to download them.

Sometimes I will need to kill any running daemons if Gradle reports failure due to connection issues:
```shell
pkill -f '.*GradleDaemon.*'
```

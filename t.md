# SemVer Rules

+ feature/.* branches increment the minorlevel (reackon default)
+ when feature is finished create tag

```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew -Preckon.stage=milestone rTC rTP "to create a new tag and push it to origin
```

+ bugfix/.* branches increment the patch level
+ when bug is solved create a tag

```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew -Preckon.scope=patch -Preckon.stage=milestone rTC rTP "to create a new tag and push it to origin
```

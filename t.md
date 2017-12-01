# SemVer Rules

## Feature branches
feature branches start with feature/

feature/.\* branches increment the minorlevel (reckon default) when baseTag is **not an release candidate(rc)  version**

when feature is finished:


**No rc version**
```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew  rTC  "to create a new tag
git checkout develop
git merge --no-ff feature/yourFeature
git push origin --tags
```

**rc versions**  increment from eg. x.y.z-rc.1 to -rc.2

**QUESTION: can an rc become new features? rc means basically close to release eg. release branch creates Pull Request to master, shouldn't there only be fixes???**
```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew  rTC -reckon.stage=rc "to create a new tag
git checkout release/currentReleaseBranch
git merge --no-ff feature/yourFeature
git push origin --tags
```


## bugfix branches
Bugfix branches start with bugfix/

bugfix/.\* branches increment the patch level unless we are on a release candidate version

when bug is solved:

**No rc version**
```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew -Preckon.scope=patch  rTC  "to create a new tag and push it to origin
git checkout develop
git merge --no-ff feature/yourFeature
git push origin --tags
```
**rc version**
```
git fetch --tags origin "to update your local tags
git merge <latest tag version> "merge latest tag onto your branches
./gradlew -Preckon.stage=rc  rTC  "to create a new tag and push it to origin
git checkout release/currentReleaseBranch
git merge --no-ff feature/yourFeature
git push origin --tags
```


## Problems
when base version is rc we can't work further on develop because localy we have the rc version and can't incremnet patch or feature level:
baseVersion = 0.2.0-rc.1
next valid version is 0.2.0 (final version)
only after that we can start patching/featuring
we could delete tags localy but that is a mess and leads to inconsitent versions and beacuse tags are sort of branch independent (though you have to merge them) if you fetch origin --tags you get ALL tags

# jitpack_publish

This is a quick script to help publish private github repos to private jitpack.io repository (subscription required)

## publish library

### Add
```
authToken={auth token from jitpack}
```
to your ~./gradle/gradle.properties file
Grab your access token from https://jitpack.io/w/user

### Add
```
GROUP={your group id}
ARTIFACT_ID={your artifact id}
```
to your library's project/gradle.properties file

Your group id will likely be com.github.{githubUserName} e.g. com.github.JRWilding
Your artifact id is whatever you want e.g. awesome_library

### Add
```
plugins {
	id "digital.wup.android-maven-publish" version "3.6.2"
}
```
To your library's build.gradle file

### Add
```
apply from: 'https://raw.githubusercontent.com/JRWilding/jitpack_publish/master/jitpack_publish.gradle'
```
To your library's project/build.gradle file

## use library as dependency

### Add
```
apply from: 'https://raw.githubusercontent.com/JRWilding/jitpack_publish/master/jitpack_publish.gradle'
dependencies {
  implementation ('{group id}:{artifact id}:{version}')
}
```
in your app project's build.gradle file using the same group and artifact ids of the library. The version can be a commit hash, tagged release or {branch}-SNAPSHOT as defined by jitpack (or look up the repo on https://jitpack.io/)

e.g.
```
apply from: 'https://raw.githubusercontent.com/JRWilding/jitpack_publish/master/jitpack_publish.gradle'
dependencies {
  implementation ('com.github.JRWilding:awesome_library:master-SNAPSHOT')
}
```

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''#!/bin/bash -xe

# DEBUG
id
pwd
ls -la
printenv | sort

# Configure git
git config --global user.name "easy-jenkins"
git config --global user.email "$(whoami)@$(hostname)"

export JAVA_HOME=
chmod a+x gradlew

./gradlew --help
./gradlew tasks

./gradlew --stacktrace --no-daemon build

# ./gradlew --info
# ./gradlew --stacktrace
# ./gradlew

# Build a debug APK
# See https://developer.android.com/studio/build/building-cmdline.html#DebugMode
./gradlew assembleDebug

# EOF'''
      }
    }
    stage('Test') {
      steps {
        echo 'TODO: Test'
      }
    }
    stage('Deploy') {
      steps {
        archiveArtifacts 'app/build/outputs/**/*.apk'
      }
    }
  }
  environment {
    ENV1 = 'VAL1'
  }
}
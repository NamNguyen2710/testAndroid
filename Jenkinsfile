pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                dir('C:\Users\User\AppData\Local\Android\Sdk\tools\bin') {
                    bat 'avdmanager create avd -n test -k system-image;android-29;google_apis;x86'
                }
                dir('C:\Users\User\AppData\Local\Android\Sdk\tools'){
                    bat 'emulator -avd test'
                }
            }
        }
        stage('run') {
            bat 'react-native run-android'
        }
        stage('clean'){
            bat 'adb emu kill'
            dir('C:\Users\User\AppData\Local\Android\Sdk\tools\bin') {
                bat 'avdmanager delete avd -n test'
            }
        }
    }
}
pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'echo no | avdmanager create avd -n test -k system-images;android-29;google_apis;x86'
                }
                dir("C:/Users/User/AppData/Local/Android/Sdk/emulator"){
                    bat 'emulator -list-avds'
                    bat 'emulator -avd test'
                }
            }
        }
        stage('run') {
            steps {
                bat 'adb root'
                bat 'react-native run-android'
            }
        }
        stage('clean'){
            steps {
                bat 'adb emu kill'
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'avdmanager delete avd -n test'
                }
            }
        }
    }
}
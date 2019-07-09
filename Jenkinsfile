pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'echo no | avdmanager create avd -n test -k system-images;android-29;google_apis;x86'
                }
            }
        }
        stage('run') {
            parallel {
                stage('run avd') {
                    dir("C:/Users/User/AppData/Local/Android/Sdk/emulator"){
                        bat 'emulator -list-avds'
                        bat 'emulator -avd test'
                    }
                }
                stage('run app') {
                    steps {
                        bat 'timeout 180'
                        bat 'adb root'
                        bat 'react-native run-android'

                    }
                }
                stage('stop emu') {
                    steps {
                        bat 'adb emu kill'
                    }
                }
            }
        }
        stage('clean'){
            steps {
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'avdmanager delete avd -n test'
                }
            }
        }
    }
}
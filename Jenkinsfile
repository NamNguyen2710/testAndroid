pipeline {
    agent any
    stages {
        stage('clean'){
            steps {
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'avdmanager delete avd -n test'
                }
            }
        }
        stage('build') {
            steps {
                bat 'npm install react-native-cli'
                dir("C:/Users/User/AppData/Local/Android/Sdk/tools/bin") {
                    bat 'echo no | avdmanager create avd -n test -k system-images;android-29;google_apis;x86'
                }
            }
        }
        stage('run') {
            parallel {
                stage('run avd') {
                    steps {
                        dir("C:/Users/User/AppData/Local/Android/Sdk/emulator"){
                            bat 'emulator -list-avds'
                            bat 'emulator -avd test'
                        }
                    }
                }
                stage('run app') {
                    steps {
                        sleep 300
                        bat 'adb root'
                        bat 'react-native run-android'

                    }
                }
                stage('stop emu') {
                    steps {
                        sleep 600
                        bat 'adb emu kill'
                    }
                }
            }
        }
    }
}
pipeline {
    agent {
        node{
            label 'AGENT-1'
        }
    }
    environment { 
        packageVersion = ''
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    

    stages {
        stage('Get the version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "Application Version : $packageVersion"
                }
            }
        }
        stage('Installing dependecies') {
            steps {
                sh """
                    npm install
                """
            }
        }
        stage('Build') {
            steps {
                sh """
                    ls -la
                    zip -r catalogue.zip ./* -x ".git/" -x ".zip"
                    ls -ltr
                """                
            }
        }
    }
    post { 
        // always { 
        //     echo 'I will always say Hello again!'
        // }
        failure { 
            echo 'Script is failed'
        }
        success { 
            echo 'Hey Script is success!'
        }
    }
}


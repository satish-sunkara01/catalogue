pipeline {
    agent {
        node{
            label 'AGENT-1'
        }
    }
    environment { 
        packageVersion = ''
        nexusURL = '172.31.5.163:8081'
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    parameters {
            booleanParam(name: 'Deploy', defaultValue: false, description: 'Run Deploy when it is true')
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
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'Script is failed'
        }
        success { 
            echo 'Hey Script is success!'
        }
    }
}


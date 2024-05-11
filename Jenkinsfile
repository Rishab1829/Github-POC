pipeline{
    agent {
      label "k8-slaves-node-16"
    }

    options {
      //discard after number of specified builds
      buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
      //disableConcurrentBuilds()
      //parallelsAlwaysFailFast()
      ansiColor('xterm')
      timeout(time: 60, unit: 'MINUTES')
    }
    
    stages{
        stage("Checkout"){
            steps{
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: params.BRANCH_NAME]],
                    userRemoteConfigs: scm.userRemoteConfigs
                ])
            }
        }

        stage("Check installed node vesrion"){
            steps{
                sh 'node -v'
            }
        }

        stage("Install App Dep"){
            steps{
                sh 'npm install'
            }
        }

        stage("Build App"){
            steps{
                sh 'npm run build'
            }
        }
    }
}
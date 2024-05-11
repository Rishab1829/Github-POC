pipeline{
    agent {
      label "k8-slaves-node-16"
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
    }
}
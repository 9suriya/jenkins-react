pipeline {
    agent any
    stages {
        stage('Setup ssh-agent') {
            steps {
                sh 'eval "$(ssh-agent -s)"'
                sh 'echo $SSH_AUTH_SOCK'
            }
        }

        stage('Add jenkins-react-app key') {
            steps {
                sh 'ssh-add /var/lib/jenkins/.ssh/jenkins-react-app.pem'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'sudo npm install'
     
            }
        }

        stage('Run tests') {
            steps {
                sh 'sudo npm test'
            }
        }
        stage("Deploy") {
            steps {
                sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
    }
}

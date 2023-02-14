pipeline {
    agent any
    stages {
        stage('Setup ssh-agent') {
            steps {
                sh 'eval "$(ssh-agent -s)"'
            }
        }

        stage('Add jenkins-react-app key') {
            steps {
                sh 'ssh-add /path/to/jenkins-react-app.pem'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'sudo npm install'
                sh "sudo npm run build"
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

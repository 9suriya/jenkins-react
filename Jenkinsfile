pipeline {
    agent any
    stages {
        
        

        stage('Install dependencies') {
            steps {
                sh 'npm install'
     
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

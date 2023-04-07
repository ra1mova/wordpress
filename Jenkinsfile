pipeline {
    agent {label "lamp-server"}

    stages {
        stage('Checkout') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'github-token', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                    git url: 'https://github.com/ra1mova/wordpress.git', branch: 'main', credentialsId: 'github-token'
                }
            }
        }

        stage('Install WordPress') {
            steps {
                sh 'sudo rm -rf  /var/www/html/*'
                sh 'git checkout .'
                sh 'sudo mv * /var/www/html'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }
    }
}


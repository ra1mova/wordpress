pipeline {
    agent {label "ubuntu"}

    stages {
        stage('Checkout') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'qwerty', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                    git url: 'https://github.com/ra1mova/wordpress.git', branch: 'main', credentialsId: 'qwerty'
                }
            }
        }

        stage('Install WordPress') {
            steps {
                sh 'sudo rm rf  /var/www/html/*'
                sh 'git checkout .'
                sh 'sudo rm -rf index.html /var/www/html/index.html'
                sh 'sudo mv * /var/www/html'
                sh 'sudo chown -R www-data:www-data /var/www/html'
                sh ''
            }
        }
    }
}


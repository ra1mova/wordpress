pipeline {
    agent {label "ubuntu"}

    stages {
        stage('Checkout') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'github', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                    git url: 'https://github.com/ra1mova/wordpress.git', branch: 'main', credentialsId: 'github'
                }
            }
        }

        stage('Install WordPress') {
            steps {
                sh 'git checkout .'
                sh 'sudo rm -rf index.html /var/www/html/index.html'
                sh 'sudo mv * /var/www/html'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }
    }
}


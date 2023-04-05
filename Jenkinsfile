pipeline {
    agent {label "qwerty"}

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
                sh 'sudo mv wordpress/* /var/www/html'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }
    }
}

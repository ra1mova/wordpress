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

        stage('Install WordPressss') {
            steps {
                sh 'git checkout .'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }
    }
}


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
                sh 'git clone https://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@github.com/ra1mova/wordpress.git'
                sh 'sudo rm -rf index.html /var/www/html'
                sh 'sudo mv wordpress/* /var/www/html'
                sh 'sudo rm -rf index.html /var/www/html'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }
    }
}

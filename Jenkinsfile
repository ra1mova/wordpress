pipeline {
    agent {label "lamp-slave"}

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
                sh 'curl -O https://wordpress.org/latest.tar.gz'
                sh 'tar -zxvf latest.tar.gz'
                sh 'sudo mv wordpress/* /var/www/html'
                sh 'sudo rm -rf wordpress latest.tar.gz'
                sh 'sudo chown -R www-data:www-data /var/www/html'
            }
        }

        stage('Build and Deploy') {
            steps {
                sh 'wp core update --path=/var/www/html --allow-root'
                sh 'wp plugin update --all --path=/var/www/html --allow-root'
                sh 'wp theme update --all --path=/var/www/html --allow-root'
            }
        }
    }
}

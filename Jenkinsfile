pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt
                git 'https://github.com/mandrantofit/potfolio.git' // Remplacez par l'URL de votre dépôt
            }
        }

        stage('Test') {
            steps {
                // Vérifier la syntaxe HTML
                script {
                    try {
                        sh 'npm install -g htmlhint' // Installer htmlhint globalement
                        sh 'htmlhint **/*.html' // Valider les fichiers HTML
                    } catch (Exception e) {
                        error "HTML validation failed. Please fix the errors."
                    }
                }
            }
        }

        stage('Build') {
            steps {
                // Vous pouvez ajouter des étapes de construction ici si nécessaire
                echo 'Build stage: Compiling resources or preparing assets.'
            }
        }

        stage('Deploy') {
            steps {
                // Déployer sur un serveur web ou un service de test
                echo 'Deploying to web server or test environment...'
                // Exemple de déploiement avec rsync ou autre commande de transfert
                // sh 'rsync -avz ./dist/ user@server:/path/to/deploy'
            }
        }

        stage('Monitoring') {
            steps {
                // Exemple de monitoring avec ping ou vérification de statut
                echo 'Monitoring deployed application...'
                sh 'curl -I http://your-deployed-site.com || echo "Deployment check failed."'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed. Check logs for details.'
        }
    }
}

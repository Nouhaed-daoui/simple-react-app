pipeline {
    agent any
    
    tools {
        
        NodeJS 20.8.0 'NodeJS' // Use the name you configured in Jenkins
    }

    stages {
        //stage('Checkout') {
        //    steps {
                // Check out your source code from your version control system (e.g., Git)
        //        checkout scm
         //   }
        //}

        stage('Build and Test') {
            steps {
                // Install Node.js and project dependencies
               
               
                // Build your React application
                sh 'npm run build'

                // Run tests (if you have test scripts in your package.json)
                sh 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build a Docker image for your React application
                sh 'docker build -t my-react-app .'
            }
        }

        stage('Deploy to Local Docker') {
            steps {
                // Deploy the Docker container to your localhost
                sh 'docker run -d -p 8081:80 my-react-app'
            }
        }
    }

    post {
        success {
            // Optionally, send notifications or trigger other jobs upon success
            echo 'Deployment successful!'
        }
        failure {
            // Optionally, send notifications or take action on failure
            echo 'Deployment failed!'
        }
    }
}

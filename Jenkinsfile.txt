pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from SCM
                git branch: 'main', url: 'https://github.com/KumarBibekAnand-2023MT93273/devops-assignment.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build the code
                sh 'mvn clean package' 
            }
        }
 	stage('Compile') {
            steps {
                // Add compile commands here
                sh 'mvn compile'
                
            }
        }
	stage('Test') {
            steps {
                // Add test commands here
                sh 'mvn test' // For Maven projects
            }
        }
    }
    
    post {
        success {
            // Notify on successful build
            echo 'Build successful!'

            // We can add additional actions here, such as deploying the build artifact or sending notifications etc..
        }

        failure {
            // Notify on failed build
            echo 'Build failed!'
        }
    }
}

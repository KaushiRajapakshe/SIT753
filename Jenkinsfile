// Kaushalya_Rajapaksha - s223681886
// 6.1C - SIT753
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Compile the code and generate any necessary artifacts using Maven"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Running unit tests and integration tests"
                }
            }
            post {
                always {
                    emailext (
                        attachLog: true, 
                        to: 'kaushi.rajapakshe1@gmail.com', 
                        subject: "Unit and Integration Tests Status Email - ${currentBuild.result}", 
                        body: "Unit and Intergration Tests was ${currentBuild.result}!\n Build Number: ${currentBuild.number}\n\n",
                        mimeType: 'text/html'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo "Analyzing code using a code analysis tool using SonarQube"
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo "Performing security scan using a security scanning tool using OWASP"
                }
            }
            post {
                always {
                    emailext (
                        attachLog: true, 
                        to: 'kaushi.rajapakshe1@gmail.com', 
                        subject: "Security Scan Status Email - ${currentBuild.result}", 
                        body: "Security Scan was ${currentBuild.result}!\n Build Number: ${currentBuild.number}\n\n"
                    )
                }
            }
        }
        stage('Deploy Tests on Staging') {
            steps {
                script {
                    echo "Deploying the application to a staging server using AWS EC2 instance"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on the staging environment"
                }
            }
            post {
                always {
                    emailext (
                        attachLog: true, 
                        to: 'kaushi.rajapakshe1@gmail.com', 
                        subject: "Integration Tests Status Email on Staging - ${currentBuild.result}", 
                        body: "Intergration Test on Staging was ${currentBuild.result}!\n Build Number: ${currentBuild.number}\n\n"
                    )
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to a production server AWS EC2 instance"
            }
        }
    }
}
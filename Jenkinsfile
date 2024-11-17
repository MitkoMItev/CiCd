pipeline{
    agent any


    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/MitkoMItev/CiCd'
            }
        }

        stage("Install dependencies"){
            steps{
                script{
                    bat 'npm install'
                }
            }
        }

        stage('Start app'){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8089'
                    bat 'npm test'
                }
            }
        }
    }

    post {
        always{
            echo "CI pipeline"
        }
    }
}

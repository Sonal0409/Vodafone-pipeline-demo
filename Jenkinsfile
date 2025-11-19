pipeline{
    agent any 
    tools{
        maven 'mymaven'
    }
    stages{
        stage('Checkout Code'){

            steps{
              git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }

        }
        stage('Compile the code'){
            steps{
                sh 'mvn compile'
            }
        }
         stage('Review the code'){
            steps{
                sh 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
                }
            }
        }
         stage('Test the code'){
            steps{
                sh 'mvn test'
            }
        }
         stage('Package the code'){
            steps{
                sh 'mvn package'
            }
        }
    }
}

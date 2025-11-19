pipeline{
    agent any 
    tools{
        maven 'mymaven'
    }
    parameters{
        choice(name: 'ENV',choices: ["","Dev","QA"])
    }
    stages{

        stage('Test the code'){
            when{  // if keyword
                expression{  //condition
                    params.ENV == "QA"  // paramter value given at runtime
                }
            }
            steps{
                git https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh 'mvn test'
            }
        }

          stage('Review the code'){
             when{
                expression{
                    params.ENV == "Dev"
                }
            }
            steps{
                sh 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
                }
            }
        }

    }
}

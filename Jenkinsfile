pipeline{
    
    tools{
        maven 'mymaven'
        jdk 'myjava'
    }
    agent any
    stages{
        stage('Clone A Repo'){
            steps{
                git 'https://github.com/VenkataNarasimha19/DevOpsClassCodes.git'
            }
        }
        stage('Compile the code')
        {
            steps{
                sh 'mvn compile'
            }
        }
        stage('Code Review')
        {
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage('Unit Test')
        {
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }    
        stage('package')
        {
            steps{
                sh 'mvn package'
            }
            post{
                success{
                    jacoco()
                }
            }
        }
    }
        
}

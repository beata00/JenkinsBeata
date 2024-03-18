pipeline {
    agent any

    stages {
            stage('Build') {
                    steps {
                        bat "mvn compile"
                }
            }
            
            stage('Test') {
                    steps {
                        bat "mvn test"
            }
            }

            stage('Post Test') {
                   steps {
                
                    jacoco(
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*',
                    )
                    junit '**/TEST*.xml'
                }
            }  

            stage('Run Robot') {
                steps {
                    bat "robot C:/Users/betty/.jenkins/workspace/BeataJenkins/Selenium/Lab2.robot"
                }
                post {
                    always  {
                        robot outputPath:'C:/Users/betty/.jenkins/workspace/BeataJenkins' , passThreshold: 80.0
                    }
                }
            }
        }
    }

            




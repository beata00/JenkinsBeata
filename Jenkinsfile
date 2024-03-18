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
                    bat "robot C:\Users\betty\.jenkins\workspace\BeataJenkins\Selenium\Lab2.robot"
                }
                post {
                    always  {
                        robot robot outputPath: '.', logFileName: 'log.html', outputFileName: 'output.xml', reportFileName: 'report.hml', passThreshold: 100, unstableThreshold: 75.0
                    }
                }
            }
        }
    }

            




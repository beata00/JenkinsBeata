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
        }
    }
}
            




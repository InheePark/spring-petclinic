pipeline {
    agent any
    
    triggers {
        cron('H */10 * * 1')
    }
    
    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        
        stage('Code Coverage') {
            steps {
                jacoco(
                    execPattern: 'target/*.exec',
                    classPattern: 'target/classes',
                    sourcePattern: 'src/main/java',
                    exclusionPattern: 'src/test*'
                )
            }
        }
    }
}

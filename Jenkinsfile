pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://44.204.187.88:8080/')], contextPath: 'welcome', war: '**/*.war'
            }
        }
    }
}

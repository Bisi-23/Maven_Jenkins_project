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
               deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://52.55.17.50:8080/')], contextPath: 'app', war: '**/*.war'
            }
        }
    }
}

pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh 'cp target/*.war /opt/tomcat/webapps/'
            }
        }

        stage('Restart Tomcat') {
            steps {
                sh '/opt/tomcat/bin/shutdown.sh || true'
                sh '/opt/tomcat/bin/startup.sh'
            }
        }
    }
}

pipeline {
  agent any
  tools {
    maven 'maven-3.8.4' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'tomcat_user', path: '', url: 'http://ec2-18-209-87-198.compute-1.amazonaws.com:8080')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}

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
          deploy adapters: [tomcat8(credentialsId: 'tomcat_user', path: '', url: 'http://dayal-test.letspractice.tk:8081')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}

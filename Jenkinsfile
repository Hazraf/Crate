pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages {
    stage ('initialize') {
      steps {
        sh '''
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
            '''
      }
    }
    
    stage ('Build') {
      steps {
      sh 'mvn clean package'
      }
    }
    
    stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json https://github.com/Hazraf/Crate.git > trufflehog'
        sh 'cat trufflehog'
      }
    
  }
}

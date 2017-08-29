pipeline {
  agent {
    node {
      label 'Backend'
    }
    
  }
  stages {
    stage('error') {
      steps {
        sh 'echo Hello Jenkins!'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn -B'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Backend": {
            sh './gradlew check'
            
          },
          "Frontend": {
            sh './gradlew check'
            
          },
          "Performance": {
            sh './gradlew check'
            
          },
          "Static": {
            sh './gradlew check'
            
          }
        )
      }
    }
  }
}
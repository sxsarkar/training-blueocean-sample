pipeline {
  agent {
    docker {
      image 'bitwiseman/training-blueocean-sample'
      args '-u root -v $HOME/.m2:/root/.m2'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh './jenkins/build.sh'
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
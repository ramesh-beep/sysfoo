pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-11-slim'
    }

  }
  stages {
    stage('build') {
      steps {
        echo 'compiling....'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit tests...'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'generating the artifact....'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'Maven 3.6.0'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
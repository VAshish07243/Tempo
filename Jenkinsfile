pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Setup Python') {
      steps {
        bat 'python --version'
      }
    }
    stage('Install dependencies') {
      steps {
        bat 'pip install -r requirements.txt || echo "No requirements file"'
      }
    }
    stage('Run script') {
      steps {
        bat 'python demo\\src\\hello.py > output.txt'
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'output.txt', allowEmptyArchive: false
    }
  }
}

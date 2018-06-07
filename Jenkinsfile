pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'echo "Hello World"'
      }
    }
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'echo "performance test"'
          }
        }
        stage('reg') {
          steps {
            sh 'echo "regression test"'
          }
        }
        stage('sec') {
          steps {
            sh 'echo "security checks test"'
          }
        }
      }
    }
    stage('build-services') {
      steps {
        build(job: 'mlp-build-app0', propagate: true)
      }
    }
  }
}
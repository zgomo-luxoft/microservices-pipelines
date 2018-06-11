pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'echo "mvn clean install"'
		sh 'echo "mvn clean test, component test"' 
		sh 'echo "mvn deploy"' 
      }


    }
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'echo "mvn component-test"'
          }
        }
     }
    }
   	stage('quality-checks'){
		parallel {
			stage('static-code-analysis'){
					steps{
						sh 'echo "static code analysis" '
					}

			}

			stage('stylechecks'){
					steps{
						sh 'echo "Execute checkstyle" '
					}
			}

			stage('security checks'){
					steps{
						sh 'echo "Execute security checks" '
					}
			}


		}
	
	}
  }
}

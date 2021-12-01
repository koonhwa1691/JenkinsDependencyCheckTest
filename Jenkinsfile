pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git '/JenkinsDependencyCheckTest'
        credentialsId: 'a593748e-d461-447f-a055-7979f14565b1'
      }
    }

    stage('OWASP DependencyCheck') {
      steps {
        dependencyCheck(additionalArguments: '--format HTML --format XML', odcInstallation: 'Default')
      }
    }

  }
  post {
    success {
      dependencyCheckPublisher(pattern: 'dependency-check-report.xml')
    }

  }
}

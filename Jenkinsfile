pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git '/koonhwa1691/JenkinsDependencyCheckTest'
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

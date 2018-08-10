pipeline {
  agent none
  stages {
    stage('Build and Test Insights Core') {
        stage('Build RHEL7 Python 2.7') {
          agent {
            docker {
              image 'centos'
            }
          }
          steps {
            echo "Installing Insights..."
            sh 'pip install --user -e .[develop]'
            echo "Testing with Pytest..."
            sh 'pytest'
            echo "Testing with flake8..."   
            sh 'flake8'
          }
        }
      }
    }
}

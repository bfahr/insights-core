pipeline {
  agent none
  stages {
        stage('Build RHEL7 Python 2.7') {
          agent {
            docker {
              image 'centos'
            }
          }
          steps {
            echo "Installing Supporting files"
            sh 'yum install -y python2-pip'
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

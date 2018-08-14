pipeline {
  agent none
  stages {
        stage('Test RHEL7 Python 2.7') {
          agent {
            docker {
              image 'bfahr/centos'
            }
          }
          steps {
            sh 'virtualenv -p /usr/bin/python2 .'
            sh 'source bin/activate'
            echo "Installing Insights..."
            sh 'pip install -e .[testing]'
            echo "Testing with Pytest..."
            sh 'command -v pytest'
            sh 'pytest'
          }
        }
        stage('Flake8 RHEL7 Python 2.7') {
          agent {
            docker {
              image 'bfahr/centos'
            }
          }
          steps {
            sh 'virtualenv -p /usr/bin/python2 .'
            sh 'source bin/activate'
            echo "Installing Insights..."
            sh 'pip install -e .[flake8]'
            echo "Testing with flake8..."   
            sh 'flake8'
          }
        }
        stage('Documents RHEL7 Python 2.7') {
          agent {
            docker {
              image 'bfahr/centos'
            }
          }
          steps {
            sh 'virtualenv -p /usr/bin/python2 .'
            sh 'source bin/activate'
            echo "Installing Insights..."
            sh 'pip install -e .[docs]'
            echo "Building Docs..."   
            sh 'sphinx-build -W -b html -qa -E docs docs/_build/html'
          }
        }
  }
}

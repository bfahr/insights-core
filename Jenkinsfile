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
            echo "Installing Insights..."
            sh """
                virtualenv -p /usr/bin/python2 .env
                source .env/bin/activate
                pip install -e .[testing]
            """
            echo "Testing with Pytest..."
            sh """
                source .env/bin/activate
                pytest
            """
          }
        }
        stage('Flake8 RHEL7 Python 2.7') {
          agent {
            docker {
              image 'bfahr/centos'
            }
          }
          steps {
            echo "Installing Insights..."
            sh """
                virtualenv -p /usr/bin/python2 .env
                source .env/bin/activate
                pip install -e .[flake8]
            """
            echo "Testing with flake8..."   
            sh """
                source .env/bin/activate
                flake8
            """
          }
        }
        stage('Documents RHEL7 Python 2.7') {
          agent {
            docker {
              image 'bfahr/centos'
            }
          }
          steps {
            echo "Installing Insights..."
            sh """
                virtualenv -p /usr/bin/python2 .env
                source .env/bin/activate
                pip install -e .[docs]
            """
            echo "Building Docs..."   
            sh """
                source .env/bin/activate
                sphinx-build -W -b html -qa -E docs docs/_build/html
            """
          }
        }
  }
}

pipeline {
  agent any
  options {
    timestamps()
    disableConcurrentBuilds()
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Set Up') {
  steps {
    sh 'python3 -m venv venv'
    sh 'venv/bin/pip install --upgrade pip'
    sh 'venv/bin/pip install -r requirements.txt'
  }
}
stage('Verify') {
  steps {
    sh 'venv/bin/python -m py_compile app.py'
    sh 'venv/bin/python -c "from app import app; print(app.url_map)"'
  }
}
  }
  post {
    always {
      echo 'Pipeline finished.'
    }
  }
}

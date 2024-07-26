pipeline {
  agent any
  stages {
    stage('Source') {
      steps {
        git 'https://github.com/HassanIT2003/web-app'
      }
    }

    stage('Build') {
      steps {
        script {
          sh '''
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
'''
        }

      }
    }

    stage('Test') {
      steps {
        script {
          sh '''
source venv/bin/activate
pytest
'''
        }

      }
    }

    stage('Deploy') {
      steps {
        script {
          sh '''
npm install -g vercel
vercel --prod --token $VERCEL_TOKEN
'''
        }

      }
    }

  }
  environment {
    VERCEL_TOKEN = 'qIoz7FEytLh7oYB1KKkU354d'
  }
  post {
    success {
      echo 'Pipeline succeeded!'
    }

    failure {
      echo 'Pipeline failed!'
    }

    always {
      echo 'Pipeline finished!'
    }

  }
}
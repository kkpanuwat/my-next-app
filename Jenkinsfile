pipeline {
  agent any

  tools {
    git 'Default' // ถ้าคุณตั้งไว้ใน Global Tool Configuration
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/kkpanuwat/my-next-app.git', branch: 'main'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t my-next-app .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh '''
          docker stop my-next-app || true
          docker rm my-next-app || true
          docker run -d -p 3000:3000 --name my-next-app my-next-app
        '''
      }
    }
  }
}

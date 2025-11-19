pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        sh 'echo Compilando...'
        sh 'ls -la'
      }
    }

    stage('Test') {
      steps {
        // Simulamos tests
        sh '''
          echo Ejecutando tests...
          # aquí irían tus comandos de test reales
        '''
      }
    }

    stage('Run script') {
      steps {
        sh '''
          chmod +x script/hola.sh
          ./script/hola.sh
        '''
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts artifacts: "build-${env.BUILD_NUMBER}.txt", fingerprint: true
      }
    }
  }

  post {
    success {
      echo '✅ Todo OK'
    }
    failure {
      echo '❌ Algo falló'
    }
  }
}


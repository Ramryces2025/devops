pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build') {
      steps {
        bat 'echo Compilando...'
        bat 'dir'
      }
    }
    stage('Test') {
      steps {
        // Simulamos tests
        bat 'echo Ejecutando tests... & exit /b 0'
      }
    }
    stage('Run script') {
      steps {
        bat 'call scripts\\hola.bat'
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts artifacts: "build-${env.BUILD_NUMBER}.txt", fingerprint: true
      }
    }
  }
  post {
    success { echo '✅ Todo OK' }
    failure { echo '❌ Algo falló' }
  }
}

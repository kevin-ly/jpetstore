pipeline {
  agent any
  stages {
    stage('Récupération des sources / Git') {
      steps {
        git(branch: 'master', credentialsId: 'loginGitHub', url: 'https://github.com/kevin-ly/jpetstore.git')
      }
    }
    stage('build Maven') {
      steps {
        bat 'runmaven.bat'
      }
    }
  }
}
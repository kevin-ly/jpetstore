pipeline {
  agent any
  stages {
    stage('R�cup�ration des sources / Git') {
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
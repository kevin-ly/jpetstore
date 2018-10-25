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
	stage('Publication'){
		steps {
			nexusArtifactUploader {
				nexusVersion('nexus3')
				protocol('http')
				nexusUrl('localhost:8081/')
				groupId('jpetstore')
				version('1.0')
				repository('maven-releases')
				credentialsId('nexus')
				artifact {
					artifactId('jpetstore')
					type('war')
					classifier('debug')
					file('target/jpetstore.war')
				}
			}
		}
	}
  }
}
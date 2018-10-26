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
		bat(script: 'runmaven.bat', encoding: 'utf-8')
      }
    }
	stage('qualim�trie'){
		steps{
			bat(script: 'runmaven.bat', encoding: 'utf-8')
		}
	}
	stage('Publication'){
		steps {
			nexusArtifactUploader artifacts: [
				[artifactId: 'jpetstore', classifier: 'debug', file:'target/jpetstore.war', type: 'war']
			],
			credentialsId: 'nexus', 
			groupId: 'jpetstore',
			nexusUrl: 'localhost:8081/',
			nexusVersion: 'nexus3',
			protocol: 'http',
			repository: 'maven-snapshots',
			version: '1.0-SNAPSHOT'
		}
	}
  }
}
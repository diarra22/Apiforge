pipeline {
    agent any 
	parameters{
		string(name: 'Nom_branche', defaultValue: 'fausse', description: 'Nom de la banche Git.')
	}
	stages{	
		stage('Checkout') {
			steps{
				deleteDir()
				dir('forge'){
						git url: 'https://github.com/diarra22/Apiforge.git', branch:"${params.master}", credentialsId: 'Apiforge'
				}
			}
		}
		stage('Build') {
		    steps {
		    withMaven(maven: 'maven3', mavenLocalRepo: 'C:/Users/utilisateur/.m2/repository') {
			  dir('forge'){
				    	bat "mvn install"
				    }
			}
		    }
		}        
    }
}

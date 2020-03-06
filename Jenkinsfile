pipeline {
    agent any 
	parameters{
		string(name: 'master', defaultValue: 'fausse', description: '')
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
			echo 'Hello world!' 
		    }
		}        
    }
}

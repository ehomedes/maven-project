pipeline{
    agent any
    
    tools{
        maven 'localMaven'
    }
    
    stages {
        
        stage('maven-project - Checkout'){
            steps {
 	            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/ehomedes/maven-project.git']]]) 
            }
	    }
	    
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
            
            post{
                success{
                    echo 'Guardar war'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
                
            }
        }
    }
}

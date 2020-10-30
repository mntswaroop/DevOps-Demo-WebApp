pipeline { 
    agent any 
	tools{
            maven 'maven'
            jdk 'java'
     }
    stages { 
	    
       stage('Scm Checkout') {            
	    steps {
               checkout scm
		  }	
           }
        stage('Build') { 
            steps {  
               sh 'mvn clean package'
	       echo 'This is a minimal pipeline to test building of a project' 
             }
        }
    }
}

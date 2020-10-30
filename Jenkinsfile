pipeline { 
    agent any 
	tools{
            maven 'maven 3'
            jdk 'java 8'
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

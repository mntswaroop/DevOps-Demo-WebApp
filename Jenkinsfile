pipeline { 
    agent any  
   stages {	
	   stage('Scm Checkout') {            
		    steps {
                  checkout scm
		   }	
           }
   }
    stages { 
        stage('Build') { 
            steps { 
               sh 'mvn clean package'
               echo 'This is a minimal pipeline to test building of a project' 
            }
        }
    }
}

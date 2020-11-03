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
	       echo 'Code checkout' 
		  }	
           }
        stage('Build') { 
            steps {  
               sh 'mvn clean package'
	       echo 'Compiling the project' 
             }
        }
	stage('Deploy to QA') { 
            steps {  
               deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://34.82.63.182:8080/')], contextPath: '/QAWebapp', war: '**/*.war'
	       echo 'Deploying to QA environment' 
             }
        }
        stage('Performing UI Tests') { 
		steps {
		  sh 'mvn test'
	          echo "Performing UI tests"
		}
	   }
    }
}

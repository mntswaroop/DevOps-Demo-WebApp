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
	   stage('Code Quality Check via SonarQube') {
            steps {
                script {
                    def scannerHome = tool 'sonarqube';
                     withSonarQubeEnv("sonarqube") {
                     sh "${tool("sonarqube")}/bin/sonar-scanner \
                     -Dsonar.sources=. \
                     -Dsonar.tests=. \
                     -Dsonar.projectKey=. \
                     -Dsonar.inclusions=**/test/java/servlet/createpage_junit.java \
                     -Dsonar.test.exclusions=**/test/java/servlet/createpage_junit.java \
                     -Dsonar.login=admin \
                     -Dsonar.password=admin \
                     -Dsonar.host.url=http://35.230.23.176:9000 \n"
                    }
                }
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
		  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '\\functionaltest\\target\\surefire-reports', reportFiles: 'index.html', reportName: 'UI-Test', reportTitles: ''])
	          echo "Performing UI tests"
		}
	   }
    }
}

pipeline { 
    agent any  
    stages { 
        stage('Build') { 
            steps { 
               sh 'mvn clean'
               echo 'This is a minimal pipeline to test building of a project' 
            }
        }
    }
}

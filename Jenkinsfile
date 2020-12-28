pipeline {
  agent any
  stages {
    stage('Maven Compile'){
        steps{
            echo 'Project compile stage'
            bat label: 'Compilation running', script: '''mvn compile'''
               }
    }
 
    stage('Unit Test') {
       steps {
            echo 'Project Testing stage'
            bat label: 'Test running', script: '''mvn test'''
        
       }
       }
 
    stage('Maven Package'){
        steps{
            echo 'Project packaging stage'
            bat label: 'Project packaging', script: '''mvn package'''
        }
    }
  
     stage('Jacoco Coverage Report') {
            steps{
                    jacoco()
        }
    }
     
    stage('SonarQube'){
        steps{
                bat label: '', script: '''mvn sonar:sonar \
                -Dsonar.host.url=http://localhost:9000 \
                -Dsonar.login=dcd63ff8c30a9071f0cafabfd15cda434314673a'''
            }
           }    
 
   }
}
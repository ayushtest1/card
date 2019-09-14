@Library('pipeline-library-demo')_


node ('maven-label'){
   def mvnHome
   stage('shared library')
   {
     sayHello 'Ayush'      
   }
   stage('Preparation') { 
      
      git 'https://github.com/ayushtest1/card.git'
      
      mvnHome = tool 'maven-3.6.1'
   }
   stage('Build') {
      withEnv(["MVN_HOME=$mvnHome"]) {
         if (isUnix()) {
            sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
         } 
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }

}

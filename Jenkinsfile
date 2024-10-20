
pipeline
{
  agent any

  stages
  {
    stage('SCM Checkout')
    { 
      steps
      {
        git branch : 'master', url: 'https://github.com/HarshGawade11/mavenproject.git'
      }
    }

    stage('compile code')
    {  
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true) 
      { sh 'mvn compile'}}
      
    }

    stage('Code testing')
    {  
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn test'}}
      
    }

    stage('Build Package')
    {  
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true)
      { withSonarQubeEnv(credentialsId: 'Sonarqube' , installationName: 'Sonarqube') {
        
         sh 'mvn clean -B -DskipTests Sonarqube:Sonarqube package'
      }}}

    }

    stage('Deploy Code')
    {  
      steps{sshagent (['CICD']){
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@10.0.0.211:/usr/share/tomcat/webapps'}
      }
    }
    


    stage('print a message')
    {  
      steps
      {
         sh 'echo this is pipeline type job'
      }
    }
  }
}

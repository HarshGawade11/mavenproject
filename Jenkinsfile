
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

    stage('Build the Package')
    {  
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn clean -B DskipTests package'}}
    }

    stage('Deploy Code')
    {  agent{label : 'JAVA'}
      steps{sshagent (['CICD']){
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@10.0.0.211:/usr/share/tomcat/webapps'}
      }
    }
    

  }
}


pipeline
{
  agent none

  stages
  {
    stage('SCM Checkout')
    { agent{label : 'JAVA'}
      steps
      {
        git branch : 'master', url: 'https://github.com/HarshGawade11/mavenproject.git'
      }
    }

    stage('compile code')
    {  agent{label : 'JAVA'}
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true) 
      { sh 'mvn compile'}}
      
    }

    stage('Code testing')
    {  agent{label : 'JAVA'}
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn test'}}
      
    }

    stage('Build Package')
    {  agent{label : 'JAVA'}
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA-HOME', maven: 'MVN-HOME', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn clean -B -DskipTests package'}}

    }

    stage('Deploy Code')
    {  agent{label : 'JAVA'}
      steps{sshagent (['CICD']){
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@10.0.0.211:/usr/share/tomcat/webapps'}
      }
    }
    


    stage('print a message')
    {  agent{label : 'JAVA'}
      steps
      {
         sh 'echo this is pipeline type job'
      }
    }
  }
}

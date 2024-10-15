
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
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'Jdk-home', maven: 'MVN-home', mavenSettingsConfig: '', traceability: true) 
      { sh 'mvn compile'}}
      
    }

    stage('Code testing')
    {
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'Jdk-home', maven: 'MVN-home', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn test'}}
      
    }

    stage('Build Package')
    {
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'Jdk-home', maven: 'MVN-home', mavenSettingsConfig: '', traceability: true)
      { sh 'mvn package'}}

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

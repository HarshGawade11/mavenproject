
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
<<<<<<< HEAD
      { sh 'mvn compile'}}
=======
      { sh 'mvn test'}}
>>>>>>> 96f80f3a54981fe7eb1bfa80c9f25d0587a31081
      
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

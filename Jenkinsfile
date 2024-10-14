
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

    stage('Validate the job')
    {
      steps{ withMaven(globalMavenSettingsConfig: '', jdk: 'Jdk-home', maven: 'MVN-home', mavenSettingsConfig: '', traceability: true) 
      { sh 'mvn validate'}}
      
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

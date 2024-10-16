
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
      { sh 'mvn clean -B -DskipTests package'}}

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

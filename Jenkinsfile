pipeline {
  agent any
  stages {
    stage('SCM') {
      parallel {
        stage('SCM') {
          steps {
            git 'https://github.com/gowraajay/mavenrepo.git'
          }
        }

        stage('Build') {
          steps {
            sh '/usr/share/maven/bin/mvn clean package'
          }
        }

      }
    }

    stage('Buil & QA') {
      steps {
        withSonarQubeEnv(envOnly: true, installationName: 'SonarQube', credentialsId: 'SonarToken') {
          sh '/usr/share/maven/bin/mvn deploy sonar:sonar'
        }

      }
    }

  }
}
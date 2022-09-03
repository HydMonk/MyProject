pipeline {
 agent any
 tools {
  maven 'Maven'
 }
 stages {
  stage ('Initialize') {

   steps {
    sh '''
	echo "PATH = $(PATH)"
	echo "M2_HOME = $(M2_HOME)"
     '''
    }
   }



    stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || true'
        sh 'docker run ghcr.io/trufflesecurity/trufflehog github --repo https://github.com/HydMonk/MyProject.git --json > trufflehog'
        sh 'cat trufflehog'
      }
    }



  stage ('Build') {
   steps {
   sh 'mvn clean package'
   }
   }


  }

 }

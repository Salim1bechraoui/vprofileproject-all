pipeline {
    
	agent any

	tools {
        maven "MAVEN3"
    }
	
    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'Nexus2023'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '54.172.18.146'
        NEXUSPORT = '8081'
        NEXUS_REPOGRP_ID = 'vprofile-grp-repo'

        NEXUS_LOGIN = 'nexuslogin'
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install '
                sh ' java -version'
                sh '  mvn  clean install -DskipTests'
            }
            post {
                success {
                     echo ' begin archiving.... '
                        archiveArtifacts artifacts: '**/target/*.war'                }
            }
        }




stage('UNIT Test') {
           steps {
            sh 'mvn test'
           }
        }
        
    }
}
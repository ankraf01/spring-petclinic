#!/bin/env groovy
pipeline {
  agent none 

  stages {

    stage('Deploy to Artifactory') {
      agent  {
        node {
          label 'tester'
        }
      }
      steps {
       // sh ''
        sh 'mvn deploy'
      }
    }

    stage('Deploy to QA') {
      agent {
        node {
          label 'tester'
        }
      }
      steps {
        sh 'ssh -p 2223 vagrant@192.168.0.18'
        sh 'sudo systemctl status tomcat'
      }
    }
  }
}

#!/usr/bin/env groovy
node {
 	// Clean workspace before doing anything
    deleteDir()

    try {
        stage ('Clone') {
      	checkout scm: [$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: '9f11a969-5319-44d6-aac3-b4716829bc14']],url: 'git@github.com:kbiswas81/Playground.git'] 
        }


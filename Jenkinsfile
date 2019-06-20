#!/usr/bin/env groovy
node {
 	// Clean workspace before doing anything
    deleteDir()

    try {
        stage ('Clone') {
      	 git([url: 'git@bitbucket.org:company/repo.git', branch: 'master', credentialsId: '12345-1234-4696-af25-123455'])
        }


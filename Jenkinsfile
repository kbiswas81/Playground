node {
 	// Clean workspace before doing anything
    deleteDir()

    try {
        stage ('Clone') {
		     dir('/home/jenkins')
        	 git([url: 'git@github.com:kbiswas81/Playground.git', branch: 'master', credentialsId: '9f11a969-5319-44d6-aac3-b4716829bc14', path: '/home/jenkins'])
 
        }
        stage ('Build') {
        	sh "echo 'shell scripts to build project...'"
        }
        stage ('Tests') {
	        parallel 'static': {
	            sh "echo 'shell scripts to run static tests...'"
	        },
	        'unit': {
	            sh "echo 'shell scripts to run unit tests...'"
	        },
	        'integration': {
	            sh "echo 'shell scripts to run integration tests...'"
	        }
        }
      	stage ('Deploy') {
            sh "echo 'shell scripts to deploy to server...'"
      	}
    } catch (err) {
        currentBuild.result = 'FAILED'
        throw err
    }
}


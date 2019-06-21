node {
parameters {
        
			string(
                name: 'STOP_PATH',
                defaultValue:"/home/impadmin/test1",
                description: "Where to stop services!")
			string(
                name: 'HADDOP_DIS',
                defaultValue:"HDP",
                description: "Which Hadoop distro to be deployed HDP|CDH!")
			string(
                name: 'Env',
                defaultValue:"Dev",
                description: "Which Env to be deployed")
			
    }
try {
stage ('git-scm'){
dir ('git-scm'){
deleteDir()
git url:'git@github.com:kbiswas81/Playground.git',branch:'master',credentialsId:'9f11a969-5319-44d6-aac3-b4716829bc14'
}}

stage ('Build') {
        	steps {
        sh "ansible-playbook -i /home/impadmin/hosts -l $Env /home/impadmin/IDW_Deployment.yml -e stop=$STOP_PATH hadoop_dist=$HADDOP_DIS" 
            }
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
	




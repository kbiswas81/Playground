#!/usr/bin/env groovy
pipeline {
    agent any
    parameters {
        
			string(
                name: 'STOP_PATH',
                defaultValue:"/home/impadmin/test1",
                description: "Where to stop services!")
//			string(
 //               name: 'HADDOP_DIS',
 //               defaultValue:"HDP",
 //               description: "Which Hadoop distro to be deployed HDP|CDH!")
			
    }

    stages {
        stage ('Deploy on Dev') {
           
        steps {
        sh "ansible-playbook -i /home/impadmin/hosts -l Dev /home/impadmin/IDW_Deployment.yml -e stop=$STOP_PATH" //hadoop_dist=$HADDOP_DIS" 
            }
			}
		stage ('Deploy on QA') {
		input{
    message "Do you want to proceed for QA deployment?"
  }
    steps {
	      sh 'echo "Deploy into QA"' }
           {
          sh "ansible-playbook -i /home/impadmin/hosts -l QA /home/impadmin/IDW_Deployment.yml -e stop=$STOP_PATH" // hadoop_dist=$HADDOP_DIS" 
            }
        }
    }
}

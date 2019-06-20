#!/usr/bin/env groovy
pipeline {
dir ('/home/jenkins/CLONE'){
git(
       url: 'git@github.com:kbiswas81/Playground.git',
       credentialsId: '9f11a969-5319-44d6-aac3-b4716829bc14',
       branch: "${master}"
    ) }



    agent any
    parameters {

                        string(
                name: 'STOP_PATH',
                defaultValue:"/home/impadmin/test1",
                description: "Where to stop services!")
//                      string(
 //               name: 'HADDOP_DIS',
 //               defaultValue:"HDP",
 //               description: "Which Hadoop distro to be deployed HDP|CDH!")

    }

    
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


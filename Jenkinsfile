#!/usr/bin/env groovy
pipeline {
    agent any
    parameters {
        choice(
            choices: ['Dev' ,'Dev1' , 'QA'],
            description: 'Select Node to Deploy',
            name: 'HOST')
                        string(
                name: 'STOP_PATH',
                defaultValue:"/home/impadmin/test1",
                description: "Where to stop services!")
    }

    stages {
        stage ('Deployment Started') {
         //   if (params.HOST == "Dev")
                // Start deployment if "Dev" is requested


            steps {
                sh "ansible-playbook -i /home/impadmin/hosts -l $HOST /home/impadmin/IDW_Deployment.yml -e stop=$STOP_PATH"
                                }

                                }
            }
        }


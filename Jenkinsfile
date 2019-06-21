pipeline {
	agent any
    parameters {
        choice(
            choices: ['Dev' , 'QA'],
            description: 'Select Node to Deploy',
            name: 'HOST')
			string(
                name: 'STOP_PATH',
                defaultValue:"/home/impadmin/test1",
                description: "Where to stop services!")
    }
     stages {
        stage ('Main Stage') {
            steps {
                 sh "ansible-playbook -i /home/impadmin/hosts -l $HOST /home/impadmin/IDW_Deployment.yml -e stop=$STOP_PATH" {
                    if (params.HOST == "Dev") {
                        stage ('Stage 1') {
                            sh 'echo Stage 1'
                        }
                    }
                    if (params.HOST == "QA") {
                        stage ('Stage 2') {
                            sh 'echo Stage 2'
                        }
                    }
                }
            }
        }
    }
}

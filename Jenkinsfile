pipeline{
    agent any

    stages{
       stage('Pull'){
            steps{
                script{
                    checkout   ([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/FatmaDaas/ProjectAngular.git']]])
                    sh " npm install "
                }

            }
         }
       stage ('build'){
             steps{
                 script{
                     sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml -e 'ansible_become_password=ansible'"
                            }
                     }
             }
 stage ('docker'){
             steps{
                 script{
                     sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml -e 'ansible_become_password=ansible'"
                            }
                     }
             }
}
}

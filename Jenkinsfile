pipeline {
    agent any
    environment {
        DOCKER_HUB_REPO = "mikehj24/casestudy_part_1"
        CONTAINER_NAME = "casestudy_part_1"
        STUB_VALUE = "200"
        REGISTRY_CREDENTIAL = "dockerhub"
    } 
    

    stages {
        
        stage('Build') {
            steps {
                    //  Building new image
                    sh 'rm -rf 2020_03_DO_Boston_casestudy_part_1'
                    sh 'git clone https://github.com/mikehj122498/2020_03_DO_Boston_casestudy_part_1.git'
		    sh 'cd 2020_03_DO_Boston_casestudy_part_1'                   
                    // create new Docker repo image
                    sh 'docker build -t mikehj24/casestudy_part_1:latest .'
                }
        }
                
        stage('Publish'){
            steps{
                //  Pushing Image to Repository
                	sh 'docker push mikehj24/casestudy_part_1:latest'                              
                	echo "Image built and pushed to repository"
            }
        }
        
        
        stage('Deployment with Kubernetes') {
            steps {
                script{
                     sh 'ansible-playbook playbook.yml'
                }
            }
        }
    }
}

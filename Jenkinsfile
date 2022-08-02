pipeline {
    agent {label "lastslave"}
    

    stages 
    {
        stage('git checkout') 
        {
            steps {
   
                git 'https://github.com/SalmaTolba/node-js-app-jenkins.git'
            }
        }
        
        stage('build') {
            steps {
                sh 'docker build -f dockerfile . -t salmatolba/nodejs:latest'
            }
        }
        
        stage('artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'username')]){
                sh 'docker login -u ${username} -p ${pass}'
                sh 'docker push salmatolba/nodejs:latest'
            }                                                       
           }
        }
        
        stage('deloy') {
            steps 
            {

                sh 'kubectl create namespace my-app'
                sh 'kubectl apply -f ./dep2.yaml -n my-app'
                sh 'kubectl apply -f ./servicelb2.yaml -n my-app'
                
            }
           }
        }
}
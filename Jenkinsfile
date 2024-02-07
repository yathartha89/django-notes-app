pipeline {
    agent any
    stages{
        stage("cloning the code"){
            steps{
                echo "cloning from github"
                git url:"https://github.com/yathartha89/django-notes-app.git/", branch:"main"
                
            }
        }    
        stage("building the code"){
            steps{
                echo "building the image"
                sh "docker build -t note-python-app:latest3.0 ."
            }
        }
        stage("pushing the code to dockerhub"){
            steps{
                echo "pushing the image to dockerhub"
                sh 'docker login -u yatharthavijay5@gmail.com -p Narula@89'
                sh 'docker tag note-python-app:latest3.0 yatharthavijay/my-apps:latest-python-app3.0'
                sh 'docker push yatharthavijay/my-apps:latest-python-app3.0'
                }
            
        }
        stage("deploying the code"){
            steps{
                echo "deploying the container"
                sh 'docker-compose -f docker-compose.yml down'
                sh 'docker-compose -f docker-compose.yml up -d'
            }
        }
    }   
    
}

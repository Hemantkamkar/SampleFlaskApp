pipeline {
    agent {
        label 'ec2' // agent = where the job will run on a  which worker node
    }

    stages { // Stages = "collection of jobs"
        stage('Download/clone the source repo from github') { //job1
            steps { // each job will have multiple steps
                git branch: 'main', url: 'https://github.com/Hemantkamkar/SampleFlaskApp.git'
            }
        }
        stage('Install pip3') { //job2
            steps {
                sh 'yum install python3-pip -y'
            }
        }
        stage('Install dependencies') { //job3
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('Execute flake8 scan and execute unit tests') { //job4

            steps {
                sh 'flake8'
                sh 'pytest'
            }
        }
        stage('Build docker image') { //job5
            steps {
                sh 'docker build -t mywebimg:latest .'
            }
        }
        stage('Run Docker container') { //job6
            steps {
                sh 'docker rm -f webos'
                sh 'docker run -dit --name webos -p 80:80 mywebimg:latest'
            }
        }
        stage('Successful deployment') { //job7
            steps {
                echo 'Application deployed successfully'
            }
        }
    }
}
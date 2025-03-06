pipeline{
    agent any

    tools{
        maven 'maven3'
    }

    stages{
        satage{
            steps('clean workspace'){
                cleanWs()
            }
        }
    }

    stages{
        stage('clone'){
            steps{
                git 'https://github.com/priyanka462002/chatroom.git'
            }
        }
        stage('compile'){
            steps{
                sh 'mvn clean compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stages{
            steps{
                sh 'trivy fs --format table -o fs.html .'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run the application'){
            steps{
                sh 'cd target && mv *.war /usr/local/tomcat/webapps/ROOT.war'
            }

        }
    }
}
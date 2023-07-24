// jenkins pipeline script
// pipeline with stages compile, test, build and echo message in the stages
// use maven to compile, test and package the application
// use docker to build the image and push to docker hub
// define environment variables mavenhome and dockerhome for the tools in jenkins


pipeline {
    agent any
    environment {
        mavenHome = tool 'mavenjenkins'
        dockerHome = tool 'dockerjenkins'
        PATH = "${mavenHome}/bin:${dockerHome}/bin:${PATH}"
    }
    stages {
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Build') {
            steps {
                sh "mvn package -DskipTests"    
            }
        }
        
    }

    post{
        always{
        echo "This is a post build stage. This will always run"
    }
        success{
        echo "This is a post build stage"
    }
        failure{
        echo "This is a post build stage"
    }
   -}
}


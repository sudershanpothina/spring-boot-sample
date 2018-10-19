pipeline{
    agent any
    tools {
        gradle 'GRADLE_LATEST' 
    }
    stages{
        stage('build'){
            steps{
                cleanWs()
                git 'git@github.com:sudershanpothina/spring-boot-demo.git'
                sh "gradle clean build"
            }
        }
        stage('deploy'){
            steps{
                withEnv(['JENKINS_NODE_COOKIE=dontkill']) {
                    sh 'nohup java -jar build/libs/spring-boot-example-2.17.1-SNAPSHOT.jar &'
                }  
            }
        }
    }
}
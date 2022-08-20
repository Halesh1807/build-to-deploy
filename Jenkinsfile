pipeline{
    agent any
    tool{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            step{
                sh 'mvn clean packege'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveartifacts Artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(path: '', url: 'http://3.109.207.104:8080/')], contextPath: null, war: '**/*.war'
            }            
        }
    }

}

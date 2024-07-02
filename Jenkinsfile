pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'

            }
            post{
                sucess{
                echo "Archiving the Artifacts"
                archiveArtifacts artifacts:'**/target/*war'
                }
            }
        }
        stage('deploy to tomcate server'){
            steps{
            deploy adapters: [tomcat9(credentialsId: 'tomcatcredintialss', path: '', url: 'http://107.20.72.86:8080/manager/html')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
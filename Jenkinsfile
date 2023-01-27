pipeline {
  agent 
    {
        label 'slave'
    }      
    tools {
        //configure gradle in jenkins and name it as Gradle_latest
        maven "MAVEN_LATEST" 
    }

    stages {
        stage('MVN Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'mvn package'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- uploading --------------->'
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'jb-hello-world-maven', 
                        classifier: '', 
                        file: 'target/simple-app-0.2.0.jar', type: 'jar'
                    
                    ]
                ], 
                credentialsId: 'nexuslogin', 
                groupId: 'org.springframework', 
                nexusUrl: '172.31.39.245:8080', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'http://ec2-3-110-143-205.ap-south-1.compute.amazonaws.com:8081/repository/maven-snapshots/', 
                version: '1.0-SNAPSHOT'
                echo '<------------- upload completed --------------->'
                    
                
            }
        }

    }
}

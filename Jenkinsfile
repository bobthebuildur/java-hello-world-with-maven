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
                        file: 'target/jb-hello-world-maven-0.2.0.jar', type: 'jar'
                    
                    ]
                ], 
                credentialsId: 'nexuslogin', 
                groupId: 'org.springframework', 
                nexusUrl: '172.31.39.245:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'maven-test-snapshot', 
                version: '0.2.0'
                echo '<------------- upload completed --------------->'
                    
                
            }
        }

    }
}

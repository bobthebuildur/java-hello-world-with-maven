  pipeline {
  agent 
    {
        label 'slave'
    }      
    tools {
        maven "MAVEN_LATEST" 
    }

    stages {
        stage('MVN Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'mvn clean install'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- uploading --------------->'
                nexusArtifactUploader artifacts: [[artifactId: 'jb-hello-world-maven', classifier: '', file: 'samplejava/target/jb-hello-world-maven-0.2.0.jar', type: '.jar']], credentialsId: 'nexuslogin', groupId: 'org.springframework', nexusUrl: 'ec2-3-110-143-205.ap-south-1.compute.amazonaws.com:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-test-snapshot', version: '0.2.0'
                echo '<------------- upload completed --------------->'
                    
                
            }
        }

    }
}

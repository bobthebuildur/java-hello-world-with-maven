   pipeline {
  agent any 
          tools {
        maven "MAVEN_LATEST" 
        
    }

    stages {
        stage('MVN Build') {
            steps {
                echo '<--------------- Building  Started --------------->'
                sh 'mvn clean install'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- uploading --------------->'
                nexusArtifactUploader artifacts: [
                    [artifactId: 'jb-hello-world-maven', 
                    classifier: '', file: 'target/jb-hello-world-maven-0.2.0.jar', 
                    type: '.jar']], 
                credentialsId: 'nexuslogin', 
                groupId: 'org.springframework', 
                nexusUrl: 'ec2-3-110-147-3.ap-south-1.compute.amazonaws.com:8081/repository/maventest-snapshot/', 
                nexusVersion: 'nexus2', 
                protocol: 'http', 
                repository: 'maventest-snapshot', 
                version: '0.4.0'
                echo '<------------- upload completed --------------->'
                    
                
            }
        }

    }
}

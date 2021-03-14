node {
    def mvnHome
    stage('checkout') { // for display purposes
        // Get some code from a GitHub repository
       git 'https://github.com/WebCiCdPipeline/demo-spring-boot.git#master'
       
    }
    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2') {
        stage('Build') {
            sh 'mvn -B'
        }
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
}

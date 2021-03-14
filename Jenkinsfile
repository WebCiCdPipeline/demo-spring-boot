

node {
    stage('checkout'){
    git branch: 'main', url:  'https://github.com/WebCiCdPipeline/demo-spring-boot.git'
       
    }
    docker.image('docker-maven:adoptopenjdk-11').inside('-v $HOME/.m2:/root/.m2') {
        stage('Build') {
            sh 'mvn -B clean install'
        }
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
}

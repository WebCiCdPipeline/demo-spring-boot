

node {
    stage('checkout'){
    git branch: 'main', url:  'https://github.com/WebCiCdPipeline/demo-spring-boot.git'
       
    }
    docker.image('maven:3-adoptopenjdk-11').inside('-v $HOME/.m2:/root/.m2') {
        stage('Build') {
            sh 'mvn -B clean install'
        }
    }
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("getintodevops/hellonode")
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
}


properties([
    parameters([
        gitParameter(branch: '',
                     branchFilter: 'origin/(.*)',
                     defaultValue: 'main',
                     description: '',
                     name: 'BRANCH',
                     quickFilterEnabled: false,
                     selectedValue: 'NONE',
                     sortMode: 'NONE',
                     tagFilter: '*',
                     type: 'PT_BRANCH')
    ])
])
node {
    stage('checkout'){
    git branch: "${params.BRANCH}", url:  'https://github.com/WebCiCdPipeline/demo-spring-boot.git'
       
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

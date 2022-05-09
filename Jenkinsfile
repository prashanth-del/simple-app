pipeline{



    agent any
    tools{
        maven 'Maven_3.8.5'
    }
    stages{
          stage('Build'){
              steps{
                    sh script: 'mvn clean package'
              }
              }
              stage('Upload War to Nexus'){
                  steps{
                        nexusArtifactUploader artifacts: [

                        [ artifactId: 'simple-app',
                          classifier: '',
                          file: 'target/simple-app-1.0.0.war', type: 'war']],
                          credentialsId: 'nexus3',
                          groupId: 'in.javahome',
                          nexusUrl: '54.204.235.19:8081',
                          nexusVersion: 'nexus3',
                          protocol: 'http',
                          repository: 'HelloWorld-Release',
                          version: '1.0.0'
                  }
          }
    }
}

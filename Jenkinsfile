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
                        script{
                        def mavenPom = readMavenPom file: 'pom.xml'
                        nexusArtifactUploader artifacts: [
                        [
                        artifactId: 'simple-app',
                        classifier: '',
                        file: "target/simple-app-${mavenPom.version}.war", type: 'war']],
                        credentialsId: 'nexus3',
                        groupId: 'in.javahome',
                        nexusUrl: '44.203.76.86:8081',
                        nexusVersion: 'nexus3',
                        protocol: 'http',
                        repository: 'HelloWorld-Release',
                        version: "${mavenPom.version}"


                        }
                  }
          }
    }
}

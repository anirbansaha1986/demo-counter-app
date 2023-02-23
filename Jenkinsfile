pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/anirbansaha1986/demo-counter-app.git'
                }
            }
        }

        stage('Unit testing'){
            
            steps{
                
                script{
                    
                    sh '''
                            export MAVEN_HOME=/opt/maven
                            export PATH=$PATH:$MAVEN_HOME/bin
                            mvn --version
                            mvn test
                        '''
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh '''
                            export MAVEN_HOME=/opt/maven
                            export PATH=$PATH:$MAVEN_HOME/bin
                            mvn --version
                            mvn verify -DskipUnitTests
                    '''
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh '''
                            export MAVEN_HOME=/opt/maven
                            export PATH=$PATH:$MAVEN_HOME/bin
                            mvn clean install
                    '''
                }
            }
        }
        stage('Upload war files to nexus'){

            steps{

                script {
                    nexusArtifactUploader artifacts: 
                    [
                        [
                            artifactId: 'springboot', 
                            classifier: '', 
                            file: 'target/Uber.jar', 
                            type: 'jar'
                        ]
                    ], 
                    credentialsId: 'nexus-auth', 
                    groupId: 'com.example', 
                    nexusUrl: '34.125.160.255:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'demo-app-release', 
                    version: '1.0.0'
                }

            }
        }
        // stage('Static code analysis'){
            
        //     steps{
                
        //         script{
                    
        //             withSonarQubeEnv(credentialsId: 'sonar-api-key') {
                        
        //                 sh '''
        //                     export MAVEN_HOME=/opt/maven
        //                     export PATH=$PATH:$MAVEN_HOME/bin
        //                     mvn clean package sonar:sonar
        //                 '''
        //             }
        //         }
                    
        //     }
        // }

        // stage('Quality Gate Status'){
            
        //     steps{
                
        //         script{
                    
        //             waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api-key'
        //         }
        //     }
        // }
    }
}

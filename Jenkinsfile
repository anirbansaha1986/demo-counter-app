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
                            mvn clean package
                        '''
                    mvn test
                }
            }
        }
    }
}

//         stage('Integration testing'){
            
//             steps{
                
//                 script{
                    
//                     sh 'mvn verify -DskipUnitTests'
//                 }
//             }
//         }
//         stage('Maven build'){
            
//             steps{
                
//                 script{
                    
//                     sh 'mvn clean install'
//                 }
//             }
//         }
//         stage('Static code analysis'){
            
//             steps{
                
//                 script{
                    
//                     withSonarQubeEnv(credentialsId: 'sonar-api') {
                        
//                         sh 'mvn clean package sonar:sonar'
//                     }
//                    }
                    
//                 }
//             }
//             stage('Quality Gate Status'){
                
//                 steps{
                    
//                     script{
                        
//                         waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
//                     }
//                 }
//             }
//         }
        
// }
pipeline {
       agent{

        environment {
        USERNAME = 'ranimelhaj'
        PASSWORD = 'ranim123*'
           }
        stages{
            stage('Checkout GIT'){
                steps{
                    echo 'Pulling...';
                    git branch: 'main',
                 
                    url : 'https://github.com/RanimELHAJ/backend.git';
                             }
                             }

            stage('MVN CLEAN')
            {
                steps{
                sh  'mvn clean'
                }
            }
            stage('MVN COMPILE')
            {
                steps{
                sh  'mvn compile'
                }
            }
            stage('MVN PACKAGE'){
                          steps{
                              sh  'mvn package'
                          }
                    }
                           stage('MVN Test'){
                                              steps{
                                                  sh  'mvn test'
                                              
                                        }
                           }
                          stage('MVN deploy'){
                                              steps{
                                                  sh  'mvn deploy'
                                              
                                        }
                           }
                             

                    stage('Build docker image'){
                                                 steps{
                                                     script{
                                                        sh 'docker build -t ranimelhaj/springproject .'
                                                     }
                                                 }
                                             }

                                              stage('Docker login') {

                                                        steps {
                                                                    sh 'echo "login Docker ...."'
                                                                    sh 'docker login registry.docker.com -u ${USERNAME} -p ${PASSWORD}'
                                                                	//sh 'docker login -u ranimelhaj -p ranim123*'
                                                                 }  }


          stage('Docker push') {

                           steps {
                                sh 'echo "Docker is pushing ...."'
                               	sh 'docker push ranimelhaj/springproject'
                                  }  }

                                }







	

}}
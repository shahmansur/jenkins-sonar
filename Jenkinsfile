     

pipeline{
        agent any  
                
        stages{


              stage('Quality Gate Statuc Check'){

                steps{
                      script{
                      withSonarQubeEnv('SonarQube') { 
                      sh "mvn sonar:sonar"
                       }
                      timeout(time: 20, unit: 'SECONDS') {
                      def qg = waitForQualityGate()
                      if (qg.status != 'OK') {
                           error "Pipeline aborted due to quality gate failure: ${qg.status}"
                      }
                    }
		    sh "mvn clean install"
                  }
                }  
              }
			  }
			  }

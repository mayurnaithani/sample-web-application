def mvnHome = "tool name: 'maven3', type: 'maven'"

pipeline{

      agent any
        
        stages{

              stage('Quality Gate Status Check'){
                  steps{
                      script{
			      withSonarQubeEnv('sonarserver') { 
			      sh "${mvnHome}/bin/mvn sonar:sonar"
                       	     	}
			      timeout(time: 1, unit: 'HOURS') {
			      def qg = waitForQualityGate()
				      if (qg.status != 'OK') {
					   error "Pipeline aborted due to quality gate failure: ${qg.status}"
				      }
                    		}
		    	   // sh "mvn clean install"
		  
                 	}
               	 }  
              }	
		
            }	       	     	         
}

 pipeline {
          agent any 
	  stages    {

	  stage('clean')
	            {
		     steps {
		           echo 'this is maven clean'
			   sh 'mvn clean'                                      
			   
			   }
	            }
	  stage('build')
	            {
		    steps {
		            echo 'this is maven build'
			    sh 'mvn compile'
			    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"

			  }
	             }
	 stage('test')
	           {
		     steps {
		          input ('do u want to proceed?')
			  }
	           }
         stage('package')
	            {
		      when {
		             
			             branch "master"
			   }

	              steps {
		            echo 'this is maven package'
			    sh 'mvn package'
			    }
	             }
         stage('install')
	            {
		     steps {
		             echo 'this is maven istall'
			     sh 'mvn install'

			    }
	             }
         
	  stage('Test') {steps {
                              echo ' this is maven test'
                                sh 'mvn test'
                         } }
                          
                          
                   
          stage('parallel test')
	         {
		 parallel {
		           stage('unit test'){
			                       steps{
					             echo "first parallel code"
						     }
					       }
                          stage('integration test') {
			                        steps {
						       echo "second parallel code"
						       }
	          }}}}
      
           post {
	        always {
		   junit 'target/surefire-reports/*.xml' 
		      }
		 failure {
		    echo ' failed'
		     }
		}     
       //stage('deploy artifacts')//
                       //{steps {

//		             echo 'this is to deploy artifacts'//
//			     sh 'mvn deploy'//
                        
		       // }}//
                  
                   
     }       

pipeline 
{
   agent { label 'linux' }
   stages 
   {
	stage('Unit Tests')
	{
	    steps {
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'   
	         }
	}   
	stage('Build') 
	{    
	    steps { 
		sh 'ant -f build.xml -v'
	          }
	}   	
	stage('Deploy') 
        {  
	    steps {   
		sh 'aws s3 cp dist/rectangle*.jar s3://devopsass9/'
	          }
	}
	stage ('Report')
	{ 
	    steps {   
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awsID', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
		  {
                 sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
                  }   
	          }
	}
	   
   }

 }



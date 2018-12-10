pipeline 
{
   agent { label 'linux' }
   stages 
   {
	   stage('Unit Test'){
		   steps{
			 
			   sh 'ant -f test.xml -v'
			   junit 'reports/result.xml'
		   }
	   }
	   stage('Build') {
		   steps{
			   sh 'ant -f build.xml -v'
		   }
	   }
	   stage('Deploy') {
		   steps{
		        sh 'echo deploy'
			 sh "s3Upload(file:'rectangle*.jar', bucket:'devopsass9', path:'s3://devopsass9/')"
		   }
	   }
	   stage('Report') {
		   steps{
	 withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'jenkins-AWS', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
			   {
    sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
                      }
		   }
	   }
   }

 }



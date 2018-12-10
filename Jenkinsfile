pipeline 
{
   agent { label 'linux' }
   stages 
   {
	   stage('Unit Test'){
		   steps{
			   git credentialsId: 'id', url: 'https://github.com/verm5034/java-project.git'
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
			sh 'aws s3 cp dist/rectangle-$BUILD_NUMBER.jar s3://devopsass9/'
		   }
	   }
	   
   }

 }



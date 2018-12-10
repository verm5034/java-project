pipeline 
{
   agent { label 'linux' }
   stages 
   {
	   stage('Unit Test'){
		   steps{
			   sh 'ant -f test.xml -v'
			   sh 'reports/result.xml'
		   }
	   }
	
	   
   }

 }



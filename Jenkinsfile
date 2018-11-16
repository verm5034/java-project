pipeline {
	agent { label 'linux' }
	stages {
	stage('Unit Tests') {
	    steps {
		git 'https://github.com/verm5034/java-project.git'
		sh 'ant -buildfile test.xml' 
		sh 'ant'
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'   
	    }
	}   
	stage('Build') {    
	    steps {
		sh 'ant'   
		sh 'ant -f build.xml -v'
	    }
	}   
	
}
}


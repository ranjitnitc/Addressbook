pipeline {
    agent any
    stages {
        stage('Run Test Suite') {
            steps {
                sh '''
                    cd /home/apache-jmeter-5.3/bin
                    sh jmeter.sh -Jjmeter.save.saveservice.output_format=xml -n -t /home/mytestresults.jmx -l /home/testresults.jtl
                '''    
            }
        }
        
        stage('Publish perfomance Results'){
            steps{
            perfReport filterRegex: '', sourceDataFiles: '/home/testresults.jtl'
            }
        }
       
    }
}

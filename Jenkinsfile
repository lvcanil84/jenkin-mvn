pipeline {
    agent any
    tools { 
        maven 'mymvn' 
        jdk 'myjdk' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }


        stage('SCM Checkout'){
            steps {
                git 'https://github.com/lvcanil84/jenkin-mvn.git'
            }
        }
        
        stage ('Compile Stage') {
            steps {
                sh 'mvn clean compile'
                echo 'Build Compile Successful'
                }
            }
        
        
        stage ('Build') {
            steps {
                sh 'mvn install'
                echo 'This is a minimal pipeline.'
            }
        }
        
        
        stage ('Deploy to Tomcat'){
            steps {
                sh 'sudo cp -r /var/lib/jenkins/workspace/myproject2/webapp/target/*.war /usr/local/apache-tomcat-7.0.94/webapps/'       
                }
        
    }
}

}

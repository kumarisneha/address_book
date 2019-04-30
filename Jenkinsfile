pipeline {
    agent {label 'python'} 
    
    stages {
        // stage('Initialize') {
        //   steps { }
        // }
        stage('Build') { 
            steps {
            sh 'python --version'
            sh 'make'
             }
        }
        stage('Test') { 
           steps {
           sh 'make check'
           junit 'reports/**/*.xml'
             }
        }
        // stage('Deploy Development') {
        //     when { branch 'master' } 
        //     steps { }
        // }
        stage('Deploy') {
            steps { 
            	sh 'make publish'
            }
        }
    }
}
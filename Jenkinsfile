pipeline{

    agent any 

    stages{
        stage('first'){
           steps{
            script{
                sh """
                   pwd 
                   ls
                   whoami
                   """
            }
           }
        }
    }
}
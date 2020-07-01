pipeline{
    agent any
    stages{
        stage('printenv'){
            steps{
                sh """
                printenv
                """
                script{
                    String[] a
                    a=GIT_URL.split('://')
                    echo "${a[1]}"
                }
            }
        }
    }
}
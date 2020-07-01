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
                    String[] b
                    b=GIT_BRANCH.split('/')
                    String branch
                    if (b.size() > 1){
                        branch=b[1]
                    }
                    echo "${b[0]}"
                    echo "${branch}"
                }
            }
        }
    }
}
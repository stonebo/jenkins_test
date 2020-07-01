pipeline{
    agent any
    stages{
        stage('setup env'){
            steps{
                echo "setup env"
                script{
                    String[] gitBranch
                    gitBranch = GIT_BRANCH.split('/')
                    if ( gitBranch.size() > 1){
                        env.branchName = gitBranch[1]
                    }else{
                        envbranchName = gitBranch[0]
                    }
                    env.gitUrl = GIT_URL.split('://')[1]
                }
            }
        }
        stage('testing'){
            steps{
                echo "testing success"
            }
        }
        stage('release'){
            when{
                branch comparator: 'GLOB', pattern: '**/master'
            }
            steps{
                echo "${branchName}"
                echo "${gitUrl}"
            }
        }
    }
}
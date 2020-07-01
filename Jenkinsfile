pipeline{
    agent any
    stages{
        stage('setup env'){
            steps{
                echo "setup env"
                script{
                    String[] gitBranch
                    String branchName
                    gitBranch = GIT_BRANCH.split('/')
                    if ( gitBranch.size() > 1){
                        branchName = gitBranch[1]
                    }else{
                        branchName = gitBranch[0]
                    }
                    String gitUrl
                    gitUrl = GIT_URL.split('://')[1]
                }
            }
        }
        stage('testing'){
            steps{
                echo "testing success"
            }
        }
        stage('release'){
            steps{
                echo "${branchName}"
                echo "${gitUrl}"
            }
        }
    }
}
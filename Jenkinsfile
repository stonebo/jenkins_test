pipeline{
    agent any
    parameter{
        choice
    }
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
                        env.branchName = gitBranch[0]
                    }
                    env.gitUrl = GIT_URL.split('://')[1]
                }
            }
        }
        stage('testing'){
            steps{
                echo "testing success"
                sh "printenv"
                sh "git branch"
            }
        }
        stage('release'){
            when{
                branch comparator: 'GLOB', pattern: 'master'
            }
            steps{
                echo "preview -> master"
            }
        }
        stage('preview release'){
            when{
                branch comparator: 'GLOB', pattern: 'preview'
            }
            steps{
                echo "STG -> preview"
            }
        }
        stage('prod hotfix'){
            when{
                branch comparator: 'GLOB', pattern: 'hotfix-prod-*'
            }
            steps{
                echo "hotfix -> master"
            }
        }
        stage('preview hotfix'){
            when{
                branch comparator: 'GLOB', pattern: 'hotfix-preview-*'
            }
            steps{
                echo "hotfix-preview -> preview"
            }
        }
        stage('Dev Code Merge'){
            when {
                    branch comparator: 'GLOB', pattern: 'Dev'
                }
            }
            steps{
                echo "dev branch -> STG"
            }
        }
    }
}
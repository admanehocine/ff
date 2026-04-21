pipeline {
    agent{
        docker{
            image 'mcr.microsoft.com/playwright:v1.59.1-noble'
            args '-u=root --entrypoint='
        }
    }
    parameters {
        booleanParam(name: 'istags', defaultValue: false, description: 'executer avec ou sans tags')
        choice(name: 'Tags', choices: ['@e2e', '@smoke', '@login'], description: 'Choisissez le choix de tag')
    }
    stages {
        stage('Example 1') {
            steps {
                sh 'npm install'
            }
        }
        stage('Example 2') {
            steps {
                
                script{
                    if (params.istags == true){
                        sh "npx playwright test --grep ${params.Tags}"
                    }else {
                        sh "npx playwright test"
                    }
                }    
            }
        }
    }
}
pipeline {
    agent{
        docker{
            image 'mcr.microsoft.com/playwright:v1.50.0-noble'
            args '-u=root --entrypoint='
        }
    }
    parameters {
        booleanParam(name: 'istags', defaultValue: false, description: 'executer avec ou sans tags')
        choice(name: 'Tags', choices: ['@e2e', '@smoke', '@login'], description: 'Choisissez le choix de tag')
    }
    stages {
        stage('Example') {
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
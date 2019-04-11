node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('promotion'){
        def userInput = input(
            id: 'userInput', message: 'Let\'s promote?', parameters: [
            [$class: 'booleanParam', defaultValue: 'true', description: 'Environment', name: 'env'],
            [$class: 'TextParameterDefinition', defaultValue: 'uat1', description: 'Target', name: 'target']
            ])
            echo ("Env: "+userInput['env'])
            echo ("Target: "+userInput['target'])
    }
    
    stage('Build File') {
        
        
        echo "Continuing with deployment"
        sh "echo {\\\"version\\\" : \\\"1.0.${env.BUILD_ID}\\\"} > a.json"
      
    }

    stage('Test File') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        sh 'file a.json'
    }

    stage("Push File") { 
       
            sh 'cat a.json | python -c "import sys,json;json.loads(sys.stdin.read());print \'OK\'"'
            
    }
    
}
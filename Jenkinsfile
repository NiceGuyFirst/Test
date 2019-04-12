node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('promotion'){
        def userInput = input(
            id: 'UserInput', message: 'Let\'s promote?', parameters: [
            [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Select scope A', name: 'Scope A'],
            [$class: 'TextParameterDefinition', defaultValue: 'uat1', description: 'Target', name: 'target']
            ])
            echo ("Scope A: "+userInput['Scope A'])
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
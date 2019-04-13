node {
    def app
    def scopeInput = input(
            id: 'UserInput', message: 'Select Project Scope', parameters: [
            [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Select scope A', name: 'Scope A'],
            [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Select scope B', name: 'Scope B']
            ])

    def userInput = input(
            id: 'UserInput', message: 'Project Configurations', parameters: [
            [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Select Agents', name: 'Agent A'],
            [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Select Agents', name: 'Agent B'],
            [$class: 'TextParameterDefinition', defaultValue: 'uat1', description: 'Target', name: 'target']
            ])

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Scope Selection'){
        
        echo ("Scope A: "+scopeInput['Scope A'])
        echo ("Target: "+scopeInput['target'])
    }
    
    stage('Build File') {
        if (userInput['Scope A'])
            echo("Selected Agents: " + userInput['Agent A']) 
        
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
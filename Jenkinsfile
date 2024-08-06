@Library('jenkins-shared-library') _

// Create a variable of map type and set the values
def configMap = [
    type: "nodejsEKS",
    component: "backend",
    project: "expense"
]

pipeline {
    agent any

    stages {
        stage('Branch Check') {
            steps {
                script {
                    if (env.BRANCH_NAME != null && !env.BRANCH_NAME.equalsIgnoreCase('main')) {
                        pipelineDecission.decidePipeline(configMap)
                    } else {
                        echo "Proceed with CR or NON-PROD pipeline"
                    }
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed"
        }
    }
}




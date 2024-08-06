@Library('jenkins-shared-library') _

// Create variable of map type and set the values
def configMap = [
    type: "nodejsEKS",
    component: "backend",
    project: "expense"
]

// Check if the BRANCH_NAME environment variable is null
if (env.BRANCH_NAME != null && !env.BRANCH_NAME.equalsIgnoreCase('main')) {
    pipelineDecission.decidePipeline(configMap)
} else {
    echo "Proceed with CR or NON-PROD pipeline"
}


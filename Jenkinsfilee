#!groovy
@Library('roboshop-shared-library') _

def configMap = [
    application: "nodejsVM",
    component: "catalogue"
]
if( ! env.BRANCH_NAME.equalsIgnoreCase('main')){
    pipelineDecession.decidePipeline(configMap)
}
else{
    echo "This is PRODUCTION, deal with CR process"
}
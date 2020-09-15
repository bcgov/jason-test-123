import groovy.json.JsonOutput

def APP_NAME = 'my-cool-app'
def POD_LABEL = "${APP_NAME}-${UUID.randomUUID().toString()}"

// See https://github.com/jenkinsci/kubernetes-plugin
podTemplate(label: "${POD_LABEL}", name: "${POD_LABEL}", serviceAccount: 'jenkins', cloud: 'openshift',
  containers: [
    containerTemplate(
      name: 'jnlp',
      image: 'image-registry.openshift-image-registry.svc:5000/openshift/jenkins-agent-nodejs:latest',
      resourceRequestCpu: '500m',
      resourceLimitCpu: '500m',
      resourceRequestMemory: '1Gi',
      resourceLimitMemory: '1Gi',
      workingDir: '/var/tmp',
      command: '',
      args: '${computer.jnlpmac} ${computer.name}',
      alwaysPullImage: false
    )
  ]
) {
  node("${POD_LABEL}") {
    stage('X') {
      checkout scm
    }
    
    stage('Setup') {
      echo "Setup: ${BUILD_ID}"
    
      sh "node -v"
      sh "npm -v"
      sh "printenv"
    }
  }
}

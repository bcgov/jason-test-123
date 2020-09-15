
// See https://github.com/jenkinsci/kubernetes-plugin
podTemplate(label: "xgLOBPyM", name: "xgLOBPyM", serviceAccount: 'jenkins', cloud: 'openshift',
  containers: [
    containerTemplate(
      name: 'jnlp',
      image: 'image-registry.apps.klab.devops.gov.bc.ca:5000/openshift/nodejs:latest',
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
  node("xgLOBPyM") {
    stage('X') {
      checkout scm
    }
    
    stage('Setup') {
      echo "Setup: ${BUILD_ID}"
    
      sh "node -v"
      sh "npm -v"
      sh "npm ci"
    }
  }
}

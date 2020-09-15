
// See https://github.com/jenkinsci/kubernetes-plugin
podTemplate(label: "xgLOBPyM", name: "xgLOBPyM", serviceAccount: 'jenkins', cloud: 'openshift',
  containers: [
    containerTemplate(
      name: 'jnlp',
      image: 'docker-registry.default.svc:5000/openshift/nodejs:10',
      resourceRequestCpu: '1500m',
      resourceLimitCpu: '2000m',
      resourceRequestMemory: '1Gi',
      resourceLimitMemory: '2Gi',
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

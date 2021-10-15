node {
  try {
    stage('checkout') {
      checkout([
        $class: 'GitSCM', branches: [[name: "${branch}"]],
        doGenerateSubmoduleConfigurations: false,extensions: [[$class:'CheckoutOption',timeout:30],[$class:'CloneOption',depth:0,noTags:false,reference:'',shallow:false,timeout:30]], submoduleCfg: [],
        //userRemoteConfigs: [[credentialsId: 'github', url: "${project_url}"]]
      ])
    }
    
    stage('prepare') {
      sh "git clean -fdx"
    }
    stage('compile') {
      echo "nothing to compile for hello.sh..."
    }
    stage('test') {
      sh "./test_hello.sh"
    }
    stage('package') {
      sh "tar -cvzf hello.tar.gz hello.sh"
    }
    stage('publish') {
      echo "uploading package..."
    }
  } finally {
    stage('cleanup') {
      echo "doing some cleanup..."
    }
  }
}

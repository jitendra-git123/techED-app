@Library('piper-library-os') _

node() {

  stage('prepare') {

      checkout scm

      setupCommonPipelineEnvironment script:this

           checkChangeInDevelopment script: this,changeDocumentId:'8000004864'
       }

  stage('build') {
      mtaBuild script: this
  }

  stage('neoDeploy') {
      neoDeploy script: this
  }

  stage('solmanTrCreate') {
      transportRequestCreate script:this, changeDocumentId:'8000004864',developmentSystemId: 'SM1~ABAP/001',applicationId: 'HCP'
  }
  stage('solmanTrRelease') {
      transportRequestRelease  script:this, changeDocumentId:'8000004864',developmentSystemId: 'SM1~ABAP/001',applicationId: 'HCP'
  }
}

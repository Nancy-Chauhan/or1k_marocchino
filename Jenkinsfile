@Library('librecores-pipeline-lib') import org.openrisc.ci.pipeline
def pipeline = new pipeline(steps)

node('librecores-ci-modules') {
  pipeline.dockerpull

  stage('docker run') {
    parallel {
        pipeline.dockerrun( "verilator" ,'verilator' )
        pipeline.dockerrun( "testing" , 'or1k-tests' , 'icarus', "or1k-cy or1k-ov or1k-shortjump")
    }
  }
}

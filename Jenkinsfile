def changeRequestId = "defaultChangeRequestId"
def pipelineName = "rama folder/child-1/child-2/fMultibranch-1234"

pipeline {
	agent any
	tools {
		maven "Maven" 
	}
	stages {
		stage('Build') {
			when {
				equals expected: 2, actual: 2
			}
			steps {
				echo 'Running build stage'
			}
		}
		stage('Test') {
			when {
				equals expected: 2, actual: 2
			}
			steps {
				echo 'Running test stage'
				// error 'Failing the Test stage'
			}
		}
		stage('Deploy') {
			//when {
			//	branch 'main'
			//}
			steps {
				echo 'Running deploy stage'
				//error 'Failing the Deploy stage'
				snDevOpsChange()
				sleep 60
        script {
          echo 'Inside script step...'
          //changeRequestId = snDevOpsGetChangeNumber()
          changeRequestId = snDevOpsGetChangeNumber(changeDetails: """{"build_number":"${env.BUILD_NUMBER}","pipeline_name":"rama folder/child-1/child-2/fMultibranch-1234/${env.BRANCH_NAME}","stage_name":"Deploy", "branchName":"${env.BRANCH_NAME}"}""")
          echo "Change Request Id without any attributes... ${changeRequestId}"
        }
			}
		}
		
	stage('GetChange') {
			//when {
			//	branch 'main'
			//}
			steps {
				echo 'Running deploy stage'
				//error 'Failing the Deploy stage'
				//snDevOpsChange()
				sleep 60
        script {
          echo 'Inside script step...'
          //changeRequestId = snDevOpsGetChangeNumber()
          changeRequestId = snDevOpsGetChangeNumber(changeDetails: """{"build_number":"${env.BUILD_NUMBER}","pipeline_name":"rama folder/child-1/child-2/fMultibranch-1234/${env.BRANCH_NAME}","stage_name":"Deploy", "branchName":"${env.BRANCH_NAME}"}""")
          echo "Change Request Id without any attributes... ${changeRequestId}"
        }
			}
		}	
	}
}

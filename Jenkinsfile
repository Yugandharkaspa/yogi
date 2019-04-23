pipeline {	
	agent any
	stages {
		 stage('Execute Powershell ') {
			steps {
				powershell(returnStdout: false, script: '''

					# =======================================================
					# Execute ARM template on subscription
					# =======================================================

						$applicationId = "b6ece3e2-be20-4b92-b0a9-b536b01d2802";
						$securePassword = "8tozBNR5anCMWEBG+3YUKGIhb9n1ntoY63D0NQAuW2k=" | ConvertTo-SecureString -AsPlainText -Force
						$credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $applicationId, $securePassword
						Connect-AzureRmAccount -ServicePrincipal -Credential $credential -TenantId "a8d9692c-9f22-4b14-b047-9697a8c37df7" -SubscriptionId "0c616cd0-67f8-41dc-9975-4aef1d9d8ea8"

						New-AzureRmResourceGroupDeployment -ResourceGroupName 'yel-tst1-t-rsg-poc' -TemplateUri 'https://tempstoragecmp.blob.core.windows.net/azurestack/template.json'


					''')
			}
		}
	}

}

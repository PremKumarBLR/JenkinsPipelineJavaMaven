#!/usr/bin/env groovy

node('master') {
	//stage 'Set Build Job Properties'
	//properties [[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '15', daysToKeepStr: '', numToKeepStr: '15']], [$class: 'GitLabConnectionProperty', gitLabConnection: 'Gitlab']]
	
	stage 'Checkout Code'
	checkout changelog: false, poll: false, scm: [$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '6b840d59-0135-4124-80e0-9c6dba22e854', depthOption: 'infinity', ignoreExternalsOption: true, local: '.', remote: 'http://10.20.16.135/svn/GrassCRM@HEAD']], workspaceUpdater: [$class: 'CheckoutUpdater']]
			
	stage 'Build'
	env.PATH = "${tool 'Ant'}/bin:${env.PATH}"
	sh 'ant build'
}

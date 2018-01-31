DEV_PROJ=flower
PROD_PROJ=flower-prod
APP_NAME=bgdemo
ORIGIN_TAG=latest
DEST_TAG=latest

node() {
  stage 'buildInDevelopment'
    openshiftBuild(namespace: ${DEV_PROJ}'', buildConfig: '${APP_NAME}', showBuildLogs: 'true')
  stage 'deployInDevelopment'
    openshiftDeploy(namespace: '${DEV_PROJ}', deploymentConfig: '${APP_NAME}')
  stage 'deployInTesting'
    openshiftTag(namespace: '${DEV_PROJ}', sourceStream: '${APP_NAME}',  sourceTag: '${ORIGIN_TAG}', destinationStream: '${APP_NAME}', destinationTag: '${DEST_TAG}')
    openshiftDeploy(namespace: '${PROD_PROJ}', deploymentConfig: '${APP_NAME}' )
}

#!groovy

stage 'Dev'
node {
  checkout scm
  bat 'mvn validate' 
  bat 'mvn compile'
  bat 'mvn test'
  bat 'mvn package'
  bat 'mvn --batch-mode -V -U -e clean deploy -U -DskipITs sonar:sonar -Dsonar.branch=${env.BRANCH_NAME} -Dsurefire.useFile=false'
   dir('target') {stash name: 'war', includes: 'x.war'}
   
}


stage 'simple'
node {
bat '''E: 
E:\\softwares\\curl-7.48.0-win64-mingw\\bin\\curl.exe -H "Content-Type: application/json" -X POST -d \'{"phase":"DEV-Exit", "username":"snyamars","action":"BUILD-SUCCESS","sender":"jenkins"}\' http://localhost:8080/job/subversion/build
	'''
}

stage 'readfile'
node{
  def line= readFile('C:/Users/ka268026/Downloads/DSL_Script_for_Jenkinsversion2_config.xml')
  echo line
}

stage 'approve'
input message: "Does Dev look good?"

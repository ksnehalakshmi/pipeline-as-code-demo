#!groovy

stage 'Dev'
node {
  checkout scm
  bat 'mvn validate' 
  bat 'mvn compile'
  bat 'mvn test'
  bat 'mvn package'
  
   dir('target') {stash name: 'war', includes: 'x.war'}
   
}
stage 'readfile'
node{
  def line= readFile('C:/Users/ka268026/Downloads/DSL_Script_for_Jenkinsversion2_config.xml')
  echo line
}

stage 'approve'
input message: "Does Dev look good?"

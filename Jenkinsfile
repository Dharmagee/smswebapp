node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      bat "${scannerHome}\\SonarScanner.MSBuild.exe begin /d:\"scandotnetcorewithjenkins\""
      bat "dotnet build"
      bat "${scannerHome}\\SonarScanner.MSBuild.exe end"
    }
  }
}

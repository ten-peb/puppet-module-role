node("master"){
  def repo = 'git@github.com:ten-peb/puppet-module-role.git'
  def localdir = 'role'
  stage("Initialize"){
    
    doGitClone(repo,localdir)
  }
  stage("Bundle Install"){
    dir(localdir) {
      sh("bundle install --path=vendor")
    }
  }
  stage("Validate"){
    dir(localdir) {
      sh("bundle exec rake validate")
    }
  }
  stage("Lint"){
    dir(localdir){
      sh("bundle exec rake lint")
    }
  }
  stage("Deploy"){
    build 'executeR10K'
  }
  
}
pipeline {
  agent {
    // By default run stuff on a x86_64 node, when we get
    // to the parts where we need to build an image on a diff
    // architecture, we'll run that bit on a diff agent
    label 'X86_64'
  }

  options {
    buildDiscarder(logRotator(numToKeepStr: '10', daysToKeepStr: '60'))
    parallelsAlwaysFailFast()
  }

  // Configuration for the variables used for this specific repo
  environment {
    // The directory to publish the site to
    PATH_PUBLISH = '/keybase/public/teknofile/'
  }

  stages {
    // Setup all the basic enviornment variables needed for the build
    stage("Setup ENV variables") {
      steps {
        script {
          env.EXIT_STATUS = ''
          env.CURR_DATE = sh(
            script: '''date '+%Y-%m-%d_%H:%M:%S%:z' ''',
            returnStdout: true).trim()
          env.GITHASH_SHORT = sh(
            script: '''git log -1 --format=%h''',
            returnStdout: true).trim()
          env.GITHASH_LONG = sh(
            script: '''git log -1 --format=%H''',
            returnStdout: true).trim()
        }
      }
    }

    stage('Build Site') {
      agent {
        docker {
          image 'teknofile/jekyll-builder:20220414'
          args '-v $WORKSPACE:/app'
        }
      }
      steps {
        sh '''
          cd /app
          bundle install
          jekyll build
        '''
      }
    }
    stage('Publish Site') {
      agent { 
        label 'X86_64'
      }
      steps {
        sh '''
          rsync -avtrpl ./_site/* hulk.cosprings.teknofile.net:/keybase/public/teknofile/
        '''
      }
    }
  }
  post {
    cleanup {
      cleanWs()
	    deleteDir()
    }
  }
}

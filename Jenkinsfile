pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Install deps') {
      steps {
        bat 'npm install --no-audit --no-fund --legacy-peer-deps newman@6 newman-reporter-htmlextra@latest'
        bat 'if not exist newman mkdir newman'
      }
    }

    stage('Run collections (parallel)') {
      parallel {
        stage('GoREST') {
          steps {
            bat '''
              npx newman run "collections\\GoREST_API.json" ^
                -e "environment\\GoREST_Env.json" ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export "newman\\gorest.html" ^
                --reporter-htmlextra-title "GoREST API - HTMLEXTRA Report"
            '''
          }
        }
        stage('Booking') {
          steps {
            bat '''
              npx newman run "collections\\Booking_API.json" ^
                -e "environment\\Booking_Env.json" ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export "newman\\booking.html" ^
                --reporter-htmlextra-title "Booking API - HTMLEXTRA Report"
            '''
          }
        }
      }
    }
  }

  post {
    always {
      writeFile file: 'newman/index.html', text: '''
<!doctype html><meta charset="utf-8"><title>Newman Reports</title>
<h1>Newman Reports</h1><ul>
  <li><a href="gorest.html">GoREST Report</a></li>
  <li><a href="booking.html">Booking Report</a></li>
</ul>'''
      archiveArtifacts artifacts: 'newman/*.html', fingerprint: true
      publishHTML(target: [reportDir: 'newman', reportFiles: 'index.html', reportName: 'Newman HTMLEXTRA'])
    }
  }
}

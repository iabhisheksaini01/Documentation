@Library('DAST') _

pipeline {
    agent any

    stages {
        stage('Install ZAP') {
            steps {
                zap_scan.installZap("2.16.1")
            }
        }

        stage('Run Zap Scan') {
            steps {
                zap_scan.runZapScan("https://juice-shop.herokuapp.com/", "results.html", 8082)
            }
        }

        stage('Archive reports') {
            steps {
                zap_scan.archiveReport("results.html")
            }
        }
    }

    post {
        success {
            script { zap_scan.sendMail(true, "results.html") }
        }
        failure {
            script { zap_scan.sendMail(false, "results.html") }
        }
    }
}

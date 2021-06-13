node("linux_server") {
    stage('Get sources from SCM') {
        git branch: 'main', changelog: false, poll: false, url: 'https://github.com/GaraninR/newsrvapp'
    }

    stage('Clean') {
        sh 'dotnet clean'
    }

    stage('Build') {
        sh 'dotnet build'
    }

    stage('Run for test') {
        sh 'dotnet run > out.log 2>&1 &'
    }
}
node("guiserver") {
    stage('Get Sources for Testing') {
        git branch: 'main', changelog: false, poll: false, url: 'https://github.com/GaraninR/newsrvapp'
    }
    stage('Test') {
        sh 'dotnet test'
    }
}
node("linux_server") {
    stage('Deploy') {
        sh 'echo "Deploy"'
    }
}
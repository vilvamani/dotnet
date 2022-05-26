pipeline {
    agent any
    
    stages {
        stage('Git Clone') {
            steps {
                cleanWs()

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vilvamani/dotnet.git']]])
            }
        }

        stage('Build & Run') {
            steps {
                bat '''
                    dotnet restore
                    rmdir /app
                    dotnet publish aspnetapp/MyWebApp.csproj -c Release -o /app
                    dotnet /app/MyWebApp.dll
                '''
            }
        }
    }
}

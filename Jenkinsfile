pipeline {
    agent { label 'dotnet6' }
    stages {
        stage ('VCS') {
            steps {
                git branch: 'uat'
                    url: 'https://github.com/pipelinesdemo/MusicStore.git' 
            }
        }
        stage ('build') {
            steps {
                sh 'dotnet restore ./MusicStore/MusicStore.csproj && dotnet build ./MusicStore/MusicStore.csproj'
            }
        }
        stage ('test') {
            {
                sh 'dotnet test --logger "junit;LogFilePath=TEST-musicstoretest.xml" ./MusicStoreTest/MusicStoreTest.csproj'
            }
        }
    }
}
node("master"){
stage("clone"){
    echo " hello suchi"
    git  credentialsId: 'gitHubCredential', url: 'https://github.com/suchi2455/petStoreAPI.git', branch: "${env.BRANCH_NAME}"
}

stage("deploy to dev"){
    sh "apictl import-api -f ./PETSTORE_API -e dev -k --preserve-provider --update --verbose"
}


stage("test"){
}

stage("deploy to upper env"){
}

}

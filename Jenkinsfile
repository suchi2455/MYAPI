node("master"){
stage("clone"){
    echo " hello suchi"
    git  credentialsId: 'SuchiGit', url: 'https://github.com/suchi2455/MYAPI.git', branch: "${env.BRANCH_NAME}"
}

stage("deploy to dev"){
    sh "apictl import-api -f ./MYAPI -e dev -k --preserve-provider --update --verbose"
}


stage("test"){
}

stage("deploy to upper env"){
}

}

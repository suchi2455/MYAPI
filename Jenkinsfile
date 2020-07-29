node("master"){
stage("clone"){
    echo " hello suchi"
    git  credentialsId: 'SuchiGit', url: 'https://github.com/suchi2455/MYAPI.git', branch: "${env.BRANCH_NAME}"
}

stage("deploy to dev"){
    bat "apictl import-api -f ./ -e dev -k --preserve-provider --update --verbose"
}


stage("test"){
}

stage("deploy to upper env"){
}

}

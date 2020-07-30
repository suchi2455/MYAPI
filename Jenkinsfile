def folderName='deployment'
def cilb='https://github.com/suchi2455/cicd.git'
def ciLibBranch='master'

node("master") {
    stage("clone") {
        echo " hello suchi"
        git credentialsId: 'SuchiGit', url: 'https://github.com/suchi2455/MYAPI.git', branch: "${env.BRANCH_NAME}"
    }
    stage("init if not") {
        //we will name folder "deployment"
        //we will check deployment folder exists
        def isDirPresent = fileExists(folderName)
        echo "Check dir present ${isDirPresent}"
        
        git credentialsId: 'SuchiGit', url: "${cilb}", branch: "${ciLibBranch}"
        
        bat "dir"
        
        if(!isDirPresent){
            bat("apictl init ${folderName} -f -d  D:\\apictl-3.1.3-windows-x64\\apictl\\default_api_template.yml --oas D:\\apictl-3.1.3-windows-x64\\apictl\\swagger.yaml")
        }

    }
    stage("deploy to dev") {
        bat "apictl import-api -f ./ -e dev -k --preserve-provider --update --verbose"
    }


    stage("test") {
    }

    stage("deploy to upper env") {
    }

}


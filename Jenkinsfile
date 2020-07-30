def folderName='deployment'
def defaultTemplate='https://gist.github.com/suchi2455/d0310c2055deaa8101a0ac88d2680357/raw/87a4f5c0c299ee8fe6136f548f91e63e649b8ca3/default_template.yml'
def swaggerurl='https://gist.githubusercontent.com/suchi2455/a0bdd515c15c0a0c051520b814026614/raw/c147c04170721747ce31339d0ab66173ac94ca93/petStoreSwagger.yml'
def ciLibBranch='master'

node("master") {
    stage("clone") {
        echo " hello suchi"
        git credentialsId: 'SuchiGit', url: 'https://github.com/suchi2455/MYAPI.git', branch: "${env.BRANCH_NAME}"
    }
    stage("init if not") {
        //1
        //we will name folder "deployment"
        //we will check deployment folder exists
        def isDirPresent = fileExists(folderName)
        echo "Check dir present ${isDirPresent}"
        
        //2  debugger        
        bat "dir"
        
        //download tdefault template file
        bat "curl ${defaultTemplate} --output defaultTemplate.yml"
        //download swagger  file
        bat "curl ${swaggerurl} --output swagger.yml"
        
        //2  debugger        
        bat "dir"
       
        if(!isDirPresent){
            echo "INIT API"
            bat("apictl init ${folderName} -f -d  defaultTemplate.yml --oas swagger.yml")
            echo "git Add ${folderName} to commit and push "
            bat "git add ${folderName}"
            echo "git commit ${folderName} to push "
            bat "git commit -m 'wso2 apictl init commit '"            
            echo "Push changed to repo ${env.BRANCH_NAME}"
            bat "git push origin ${env.BRANCH_NAME}"
        }
        else{
            echo "${folderName} already present"
            bat "tree ${folderName}"
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


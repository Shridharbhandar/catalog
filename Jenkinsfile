pipeline {
    agent any
    stages {
        stage('EB') {    
            steps {
                script{ 
                def list = ["us-east-1", "us-west-2", "us-west-1", "us-east-2", "eu-central-1", "ap-southeast-1", "ap-southeast-2", "ap-northeast-1", "ap-northeast-2", "sa-east-1", "ap-south-1"]
for(int i=0; i<=10; i++){
    withAWS(credentials: '6f14420c-23c0-4ffb-b4f5-2760d2a108f1', region: list[i]) {
        sh '''
        aws elasticbeanstalk describe-applications | jq -r '.Applications[].ApplicationName' > application.txt
        i=$(cat application.txt | wc -l) 
        if [ $i -gt 0 ];
        then
        for (( n=0; n<i; n++ ))
        do
        mapfile < application.txt
        export APP_VERSION="${MAPFILE[n]}-${BUILD_NUMBER}"
        mvn package
        aws s3 cp target/*.jar s3://ibex-catalog-eb-$AWS_DEFAULT_REGION
        aws elasticbeanstalk create-application-version --application-name ${MAPFILE[n]} --version-label "${APP_VERSION}" --source-bundle S3Bucket="sample-bucket-jenkins-testing",S3Key="/jenkins/tomcat/*.tar"

        aws elasticbeanstalk describe-environments --application-name ${MAPFILE[n]} | jq -r '.Environments[].EnvironmentName' > env.txt
        j=$(cat env.txt | wc -l)
        if [ $j -ge 0 ];
        then
        for (( a=0; a<=j; j++ ))
        do
            envi=$(awk '{print $a}' env.txt)
            aws elasticbeanstalk update-environment --environment-name "${envi}" --version-label "${APP_VERSION}"
        done
        else
        echo "No Appliucations in this region"
        fi


        done
        else 
        echo "No Environments in this region"
        fi
        '''
                            }
                        }
                    }
                }
            }
        }
    }



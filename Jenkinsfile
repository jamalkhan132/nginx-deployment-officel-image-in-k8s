#ci
pipeline {
agent any
stages{
//     stage("bring the code from scm"){   
//         steps{
            
//     # sh 'git@github.com:jamalkhan132/automation.git'
// }
//     }
stage("make pkg"){
    steps{
   sh 'zip -r artifactory-ci$BUILD_NUMBEE.zip *'
   sh 'aws s3 cp artifactory-ci$BUILD_NUMBEE.zip s3://artifactory-cicd-labs-demo-gft/'
}
}
stage("CD-DEPLOYMENT"){
    steps{
    sh 'rm -f *'   
    sh 'aws s3 cp artifactory-ci$BUILD_NUMBEE.zip .'
    sh  'unzip  artifactory-ci$BUILD_NUMBEE.zip'
    sh  'scp index.html root@172.31.82.218:/var/www/html/'

}
}
}
} 
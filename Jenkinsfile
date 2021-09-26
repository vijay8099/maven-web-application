node{
    
def mavenHome = tool name: "maven3.6.3"
stage('Checkoutcode'){
    git branch: 'development', credentialsId: 'a96f61ff-c05d-4257-b1bf-d958ac16ef47', url: 'https://github.com/vijay8099/maven-web-application.git'
}
    
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

stage('SonarQube'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}
/*
stage('Nexus'){
sh "$mavenHome/bin/mvn deploy"
}

stage('Tomcat'){
sshagent(['21946a5c-b58d-4f53-8f9d-ccf31ef119d2']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.159.66:/opt/apache-tomcat-9.0.52/webapps"
}
*/
}
stage('Email'){
emailext body: '''regards,
vijay.''', subject: 'build over ', to: 'vijayvijay205@gmail.com,vijaykumarkushalfabs@gmail.com'
}

}

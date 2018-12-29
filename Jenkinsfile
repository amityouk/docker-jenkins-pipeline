node {
  checkout scm
  env.PATH = "${tool 'Maven3'}/bin:${env.PATH}"
  stage('Package') {
    dir('webapp') {
      sh 'mvn clean package -DskipTests'
    }
  }

  stage('Create Docker Image') {
    dir('webapp') {
      docker.build("arungupta/docker-jenkins-pipeline:${env.BUILD_NUMBER}")docker && adduser docker docker

@willfarrell fix the bug please
@markqiu markqiu closed this on Dec 23, 2017
@willfarrell
Owner
willfarrell commented on Dec 23, 2017

@markqiu Just submit a PR. I'm happy to merge.
@kendokan
Contributor
kendokan commented on Jan 10

Confirmed the fix from @markqiu is functional.
kendokan added a commit to kendokan/docker-crontab that referenced this issue on Jan 10
@kendokan
fixed willfarrell#9
40b8b93
willfarrell added a commit that referenced this issue on Jan 10
@willfarrell
Merge pull request #10 from kendokan/master
147e900
@willfarrell
Owner
willfarrell commented on Jan 10

Thanks,
@amityouk

Attach files by dragging & dropping, selecting them, or pasting from the clipboard.
Styling with Markdown is supported

    }
  }

  stage ('Run Application') {
    try {
      // Start database container here
      // sh 'docker run -d --name db -p 8091-8093:8091-8093 -p 11210:11210 arungupta/oreilly-couchbase:latest'

      // Run application using Docker image
      sh "DB=`docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' db`"
      sh "docker run -e DB_URI=$DB arungupta/docker-jenkins-pipeline:${env.BUILD_NUMBER}"docker && adduser docker docker

@willfarrell fix the bug please
@markqiu markqiu closed this on Dec 23, 2017
@willfarrell
Owner
willfarrell commented on Dec 23, 2017

@markqiu Just submit a PR. I'm happy to merge.
@kendokan
Contributor
kendokan commented on Jan 10

Confirmed the fix from @markqiu is functional.
kendokan added a commit to kendokan/docker-crontab that referenced this issue on Jan 10
@kendokan
fixed willfarrell#9
40b8b93
willfarrell added a commit that referenced this issue on Jan 10
@willfarrell
Merge pull request #10 from kendokan/master
147e900
@willfarrell
Owner
willfarrell commented on Jan 10

Thanks,
@amityouk

Attach files by dragging & dropping, selecting them, or pasting from the clipboard.
Styling with Markdown is supported


      // Run tests using Maven
      //dir ('webapp') {
      //  sh 'mvn exec:java -DskipTests'
      //}
    } catch (error) {
    } finally {
      // Stop and remove database container here
      //sh 'docker-compose stop db'
      //sh 'docker-compose rm db'
    }
  }

  stage('Run Tests') {
    try {
      dir('webapp') {
        sh "mvn test"
        docker.build("arungupta/docker-jenkins-pipeline:${env.BUILD_NUMBER}").push()
      }
    } catch (error) {

    } finally {
      junit '**/target/surefire-reports/*.xml'
    }
  }
}

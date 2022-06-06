FROM jenkins/jenkins:2.332.3-jdk11
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli

USER jenkins

RUN jenkins-plugin-cli --plugins "blueocean:1.25.5 docker-workflow:1.28"

#RUN sh UPDATE_LIST=$( java -jar /root/jenkins-cli.jar -s http://127.0.0.1:8080/ list-plugins | grep -e ')$' | awk '{ print $1 }' ); 
#        if [ ! -z "${UPDATE_LIST}" ]; then 
#            echo Updating Jenkins Plugins: ${UPDATE_LIST}; 
#            java -jar /root/jenkins-cli.jar -s http://127.0.0.1:8080/ install-plugin ${UPDATE_LIST};
#            java -jar /root/jenkins-cli.jar -s http://127.0.0.1:8080/ safe-restart;
#        fi

#RUN curl -s -L http://updates.jenkins-ci.org/update-center.json | sed '1d;$d' | curl -s -X POST -H 'Accept: application/json' -d @- http://localhost:8080/updateCenter/byId/default/postBack
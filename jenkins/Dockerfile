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

RUN jenkins-plugin-cli --plugins "blueocean:1.25.5 jdk-tool:1.5 command-launcher:84.v4a_97f2027398 sshd:3.237.v883d165a_c1d3 credentials:1129.vef26f5df883c github:1.34.3 docker-workflow:1.28 kubernetes:3600.v144b_cd192ca_a_ terraform:1.0.10 sonar:2.14"

FROM jenkinsci/jenkins:2.104
USER root
RUN mkdir /var/log/jenkins
RUN mkdir /var/cache/jenkins
RUN mkdir /var/jenkins_home/.ssh
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN chown -R jenkins:jenkins /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/jenkins_home

USER jenkins


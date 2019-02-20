FROM debian:9
EXPOSE 443
EXPOSE 80
EXPOSE 22
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y curl openssh-server ca-certificates
RUN apt-get install -y postfix
RUN curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN mkdir /etc/gitlab
RUN touch /etc/gitlab/skip-auto-reconfigure
RUN apt-get install gitlab-ce=11.7.5*
RUN SKIP_POST_DEPLOYMENT_MIGRATIONS=true 
RUN echo "package['detect_init'] = false" >> /opt/gitlab/gitlab.rb
RUN echo "unicorn['worker_timeout'] = 300" >> /opt/gitlab/gitlab.rb
RUN echo "postgresql['shared_buffers'] = '1MB'" >> /opt/gitlab/gitlab.rb
COPY script.sh /usr/local/bin/
RUN ln -s /usr/local/bin/script.sh /
USER root
ENTRYPOINT ["sh"]
CMD ["./script.sh"]

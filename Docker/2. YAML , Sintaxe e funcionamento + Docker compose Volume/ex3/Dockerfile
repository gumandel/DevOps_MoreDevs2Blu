FROM httpd:latest
RUN apt-get update && \
    apt-get install -y git
RUN git clone https://github.com/dartanghan/proway.git /tmp/proway && \
    cd /tmp/proway && \
    git checkout c4640c6c3d6618b022c94f79e97dfd2d4297758c
RUN mv /tmp/proway/* /usr/local/apache2/htdocs
CMD ["httpd-foreground"]
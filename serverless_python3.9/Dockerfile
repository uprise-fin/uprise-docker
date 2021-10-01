FROM lambci/lambda:build-python3.8

RUN yum install wget -y
RUN yum install openssl-devel libffi-devel bzip2-devel -y
RUN wget https://www.python.org/ftp/python/3.9.7/Python-3.9.7.tgz
RUN tar xvf Python-3.9.7.tgz
WORKDIR Python-3.9.7/
RUN ./configure
RUN make altinstall
RUN yum -y install mysql-devel
RUN pip3.9 install poetry
RUN curl -sL https://sentry.io/get-cli/ | bash
RUN curl -sL https://rpm.nodesource.com/setup_12.x | bash -
RUN yum -y install nodejs
RUN npm install -g serverless
RUN cp /usr/lib64/mysql/libmysqlclient.so.18.0.0 ./libmysqlclient.so.18

FROM lambci/lambda:build-python3.8
RUN curl -sL https://sentry.io/get-cli/ | bash
RUN yum -y install mysql-devel
RUN curl -sL https://rpm.nodesource.com/setup_16.x | bash -
RUN yum -y install nodejs
RUN npm install -g serverless
RUN npm install -g pnpm
RUN pip install --upgrade pip
RUN pip install poetry==1.1.12
RUN cp /usr/lib64/mysql/libmysqlclient.so.18.0.0 ./libmysqlclient.so.18

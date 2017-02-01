FROM lambci/lambda-base:build

ENV LAMBDA_TASK_ROOT=/var/task \
    LAMBDA_RUNTIME_DIR=/var/runtime \
    LANG=en_US.UTF-8

ADD _docker/awslambda-mock.js /var/runtime/node_modules/awslambda/build/Release/awslambda.js

# Not sure why permissions don't work just by modifying the owner
RUN rm -rf /tmp && mkdir /tmp && chown -R sbx_user1051:495 /tmp && chmod 700 /tmp

# create home directory for the user to make sure some node packages work
RUN mkdir -p /home/sbx_user1051 && chown -R sbx_user1051:495 /home/sbx_user1051

WORKDIR /var/task

RUN npm install -g nodemon

ADD package.json .
RUN npm install

USER sbx_user1051

ENTRYPOINT nodemon --exec "node --max-old-space-size=1229 --max-semi-space-size=76 --max-executable-size=153 --expose-gc /var/runtime/node_modules/awslambda/index.js $HANDLER $EVENT"
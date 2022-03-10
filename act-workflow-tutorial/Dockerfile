FROM docker:dind


RUN apk add curl
RUN curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sh

COPY .actrc /
RUN mv /.actrc ~/.actrc
RUN mkdir /secret

WORKDIR /project

CMD /bin/sh -c "act -n ${ACTION} > /logs/dry-run.log; act ${ACTION} --secret-file=/secret/act.vault -v > /logs/run.log"

# operating system
FROM ubuntu:20.04

# get toilet and remove container during exit 
RUN apt-get update -y && \ 
    apt-get install -y toilet && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* 

ENTRYPOINT ["toilet", "-F", "border", "--gay"]

CMD ["hello world"]
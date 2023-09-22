FROM ubuntu:22.04

# url of .zip file
ARG zip_url=https://github.com/eficode-academy/devops-academy-whale/archive/refs/heads/master.zip
# update local package cache
RUN apt-get update && \
# intall wget for downloading the .zip file
    apt-get install -y wget && \
# download .zip file of github repository
    wget --output-document /tmp/repo.zip ${zip_url} && \
    apt-get remove -y wget && \
    apt-get install -y unzip && \
# unzip the downloaded repository
    unzip /tmp/repo.zip -d /tmp/ && \
    apt-get remove -y unzip && \
    mkdir /lolcat && \
#move the whale file to appropriate place
    mv /tmp/devops-academy-whale-master/whale.txt /lolcat/whale.txt && \
# delete all the other stuff we don't need
    rm -rf /tmp/devops-academy-handins-public-master && \
# install ruby to get the gem package manager
    apt-get install -y ruby && \
# install lolcat as a gem (ruby package)
    gem install lolcat && \
# colorize the whale!
    lolcat --seed=123 --force /lolcat/whale.txt > /lolcat/color_whale.txt && \
    rm /lolcat/whale.txt && \
# 'gem uninstall' must be approved interactively, so we use 'yes' to do so...
    yes | gem uninstall lolcat && \
# delete all unused gem packages
    gem cleanup && \
    apt-get remove -y ruby && \
# remove all unsued .deb packages
    apt-get autoremove -y && \
# clean out local package cache
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["cat", "/lolcat/color_whale.txt"]

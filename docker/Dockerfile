FROM node:12-buster

COPY ./ /root/core-hydra

RUN apt-get update
RUN apt-get install -y git python make g++ libjemalloc-dev

RUN cd ~/core-hydra && yarn setup

COPY docker/docker-entrypoint.sh /usr/local/bin/
RUN ln -s usr/local/bin/docker-entrypoint.sh / # backwards compat

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["testnet","genesis","auto_forge"]

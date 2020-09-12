FROM gitea/gitea:latest

RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf;\
	 apk --no-cache add --update gcc g++ python3-dev py3-pip libffi-dev asciidoc && rm -rf /var/cache/apk/*
# install any other package you need for your external renderers

RUN echo "nameserver 8.8.8.8" > /etc/resolv.conf; \
	pip3 install --upgrade pip;\
	pip3 install jupyter notebook 
# add above any other python package you may need to install


FROM ubuntu:18.04

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
		apt-transport-https \
		ca-certificates \
		curl \
		gnupg \
		sudo \
 && rm -rf /var/lib/apt/lists/*

ENV VPP_VERSION_ID 19.01

LABEL io.fd.vpp.version.id=$VPP_VERSION_ID

RUN set -eux; \
	repoUrl="https://packagecloud.io/install/repositories/fdio/1901"; \
    curl -fsSL "$repoUrl"/script.deb.sh | bash; \
	apt-get install -y -V \
		vpp \
		vpp-dbg \
		vpp-dev \
		vpp-plugins \
		vpp-api-python; \
	rm -rf /var/lib/apt/lists/*; \

RUN mkdir -p /var/log/vpp

CMD ["/usr/bin/vpp", "-c", "/etc/vpp/startup.conf"]

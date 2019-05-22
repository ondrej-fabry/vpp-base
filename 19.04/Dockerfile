FROM ubuntu:18.04

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
		apt-transport-https \
		ca-certificates \
		curl \
		gnupg \
		sudo \
 && rm -rf /var/lib/apt/lists/*

ENV VPP_VERSION_ID 19.04

LABEL io.fd.vpp.version.id=$VPP_VERSION_ID

RUN set -eux; \
	repoUrl="https://packagecloud.io/install/repositories/fdio/1904"; \
    curl -fsSL "$repoUrl"/script.deb.sh | bash; \
	apt-get install -y -V \
		vpp \
		vpp-dbg \
		vpp-dev \
		vpp-plugin-core \
		vpp-plugin-dpdk \
		vpp-api-python \
		python3-vpp-api; \
	rm -rf /var/lib/apt/lists/*; \

RUN mkdir -p /var/log/vpp

CMD ["/usr/bin/vpp", "-c", "/etc/vpp/startup.conf"]

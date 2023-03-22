FROM paperspace/gradient-base:pt112-tf29-jax0317-py39-20230125

RUN apt-get update && \
apt-get install -y curl && \
apt-get clean && \
rm -rf /var/lib/apt/lists/*

RUN curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb && \
dpkg -i cloudflared.deb

EXPOSE 8888 6006 22 8889

CMD jupyter lab --allow-root --ip=0.0.0.0 --no-browser --ServerApp.trust_xheaders=True --ServerApp.disable_check_xsrf=False --ServerApp.allow_remote_access=True --ServerApp.allow_origin='*' --ServerApp.allow_credentials=True; cloudflared service install token_name
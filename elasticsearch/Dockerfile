ARG ELK_VERSION

# https://github.com/elastic/elasticsearch-docker
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELK_VERSION}

# Add healthcheck
COPY scripts/docker-healthcheck .
HEALTHCHECK CMD sh ./docker-healthcheck

# Add your elasticsearch plugins setup here
# Example: RUN elasticsearch-plugin install analysis-icu
#RUN elasticsearch-plugin install --batch repository-s3
ARG ELK_VERSION
ENV ELKV $ELK_VERSION
RUN elasticsearch-plugin install --batch org.codelibs:elasticsearch-analysis-fess:${ELKV}; \
elasticsearch-plugin install --batch org.codelibs:elasticsearch-analysis-extension:${ELKV}; \
elasticsearch-plugin install --batch org.codelibs:elasticsearch-configsync:${ELKV}; \
elasticsearch-plugin install --batch org.codelibs:elasticsearch-dataformat:${ELKV}; \
elasticsearch-plugin install --batch org.codelibs:elasticsearch-minhash:${ELKV}

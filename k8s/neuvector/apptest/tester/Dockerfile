FROM gcr.io/cloud-marketplace-tools/testrunner:0.1.5

RUN apt-get update && apt-get install -y --no-install-recommends \
    wget \
COPY tester.sh /tester.sh

WORKDIR /
ENTRYPOINT ["/tester.sh"]

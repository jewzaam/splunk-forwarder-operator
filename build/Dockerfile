FROM registry.svc.ci.openshift.org/openshift/release:golang-1.12 AS builder

RUN mkdir -p /workdir
WORKDIR /workdir
COPY . .
RUN make gobuild

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest

WORKDIR /root/
COPY --from=builder /workdir/build/_output/bin/* /usr/local/bin/

LABEL io.openshift.managed.name="splunk-forwarder-operator" \
      io.openshift.managed.description="This operator will be responsible for deploying the splunk forwarder."

# SPDX-License-Identifier: GPL-3.0-or-later
#!BuildTag: trento/trento-checks:latest
#!BuildTag: trento/trento-checks:%%VERSION%%
#!BuildTag: trento/trento-checks:%%VERSION%%-build%RELEASE%
#!UseOBSRepositories
#!ExclusiveArch: x86_64
FROM registry.suse.com/bci/bci-base:15.6

LABEL org.opencontainers.image.source="https://github.com/trento-project/checks"

# If set to C, LC_ALL takes precedence
ENV LC_ALL=C.UTF-8

RUN mkdir --mode=0600 /tmp/trento-checks-build

WORKDIR /tmp/trento-checks-build

# checks.tar.gz is provided by OBS (build.opensuse.org)
ADD checks.tar.gz .

RUN install --directory --mode=0755 /usr/src/trento-checks
RUN install --directory --mode=0755 /usr/src/trento-checks/checks
RUN install --preserve-timestamps --mode=0644 ./checks/checks/* /usr/src/trento-checks/checks
RUN install --preserve-timestamps --mode=0755 ./checks/bin/trento-install-checks /usr/bin/trento-install-checks

WORKDIR /

RUN rm -r /tmp/trento-checks-build

ENTRYPOINT ["/usr/bin/trento-install-checks"]


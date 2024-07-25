FROM oceanbasedev/oceanbase-helper

ARG VERSION
ARG RELEASE
ARG TARGETPLATFORM
LABEL name="oceanbase-cloud-native" \
      vendor="OceanBase" \
      version=${VERSION} \
      release=${RELEASE} \
      summary="OceanBase image" \
      description="OceanBase image for using on Kubernetes" \
      maintainer="OceanBase"
RUN mkdir -p /licenses
COPY LICENSE /licenses
# support docker platform linux/amd64 and linux/arm64, mapping platform to x86_64 or aarch64
RUN if [[ ${TARGETPLATFORM} == 'linux/amd64' ]] ; then yum install -y http://mirrors.aliyun.com/oceanbase/community/stable/el/8/x86_64/oceanbase-ce-libs-${VERSION}-${RELEASE}.el8.x86_64.rpm ; else yum install -y http://mirrors.aliyun.com/oceanbase/community/stable/el/8/aarch64/oceanbase-ce-libs-${VERSION}-${RELEASE}.el8.aarch64.rpm ; fi ; yum clean all;
RUN if [[ ${TARGETPLATFORM} == 'linux/amd64' ]] ; then yum install -y http://mirrors.aliyun.com/oceanbase/community/stable/el/8/x86_64/oceanbase-ce-${VERSION}-${RELEASE}.el8.x86_64.rpm ; else yum install -y http://mirrors.aliyun.com/oceanbase/community/stable/el/8/aarch64/oceanbase-ce-${VERSION}-${RELEASE}.el8.aarch64.rpm ; fi ; yum clean all
ENV LD_LIBRARY_PATH /home/admin/oceanbase/lib
USER admin

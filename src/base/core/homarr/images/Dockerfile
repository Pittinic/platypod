ARG BUILDER_IMAGE
ARG SOURCE_IMAGE

FROM ${BUILDER_IMAGE} AS builder
COPY resources /resources
ARG ENVSUBST_TARGET_FILES=""
ARG ENVSUBST_TARGET_FOLDERS="/resources"
ARG WHOAMI_URL
RUN /envsubst.sh > /envsubst.log

FROM ${SOURCE_IMAGE} AS target
COPY --from=builder /resources /
COPY --from=builder /envsubst.log /envsubst.log

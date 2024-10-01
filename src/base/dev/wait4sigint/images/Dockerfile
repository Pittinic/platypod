FROM golang:1.21-alpine3.18 as go-builder
COPY resources/wait4sigint.go /wait4sigint.go
ARG GOOS
ARG GOARCH
RUN GOOS="${GOOS}" GOARCH="${GOARCH}" go build -v -o /wait4sigint /wait4sigint.go

FROM scratch
COPY --from=go-builder wait4sigint /
ENTRYPOINT ["/wait4sigint"]

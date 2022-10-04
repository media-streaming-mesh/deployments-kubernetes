FROM --platform=$BUILDPLATFORM golang:1.19 as builder

WORKDIR /workspace

COPY rtsp-simple-server .

RUN go mod tidy
RUN go mod download

ARG TARGETOS TARGETARCH

# Build
RUN --mount=type=cache,target=/root/.cache/go-build \
        --mount=type=cache,target=/go/pkg \
        GOOS=$TARGETOS GOARCH=$TARGETARCH go build -a -o rtsp-simple-server main.go

FROM ciscolabs/rtsp-client:dev

COPY rtsp-simple-server.yml /
COPY --from=builder /workspace/rtsp-simple-server /
COPY testsrc.mp4 /

ENTRYPOINT ["/rtsp-simple-server"]


FROM golang:1.23.2 as builder
WORKDIR /workspace
COPY backend/ .
RUN go mod tidy && CGO_ENABLED=0 go build -o app main.go

FROM node:18.20.4 as console
WORKDIR /workspace/console
COPY web-console/ .
RUN npm install && npm run build

FROM alpine:latest
WORKDIR /workspace
COPY --from=console /workspace/console/dist ./dist
COPY --from=builder /workspace/app .
COPY --from=builder /workspace/translate.json .
COPY --from=builder /workspace/googleElement.js .
ENTRYPOINT [ "./app" ]

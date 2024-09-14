# # Stage 1: Build Stage
# FROM golang:1.18-alpine AS build

# WORKDIR /app

# # Copy Go module files and download dependencies
# COPY go.mod go.sum ./
# RUN go mod download

# # Copy the rest of your application code
# COPY . .

# # Build the Go binary
# RUN go build -o main .

# # Stage 2: Runtime Stage
# FROM alpine:latest

# WORKDIR /app

# # Copy the built binary from the build stage
# COPY --from=build /app/main .

# # Expose the port that the application will listen on
# EXPOSE 8000

# # Run the Go binary
# CMD ["./main"]



FROM golang:1.19 AS build-stage

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY *.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -o /backend

FROM build-stage AS run-test-stage
RUN go test -v ./...

FROM alpine AS build-release-stage

WORKDIR /

COPY --from=build-stage /backend /backend

EXPOSE 8000


ENTRYPOINT ["/backend"]

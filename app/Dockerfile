# Build stage
FROM rust:1.94 AS builder
WORKDIR /usr/src/app

COPY Cargo.toml Cargo.lock ./
COPY src ./src

RUN cargo build --release

# Runtime stage
FROM debian:bookworm-slim
WORKDIR /app

COPY --from=builder /usr/src/app/target/release/your-binary-name /app/your-binary-name

CMD ["./app"]

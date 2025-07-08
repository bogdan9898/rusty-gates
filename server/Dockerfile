# server/Dockerfile
# --- Builder stage ---
FROM rust:1.84 as builder

WORKDIR /app
COPY . .

RUN cargo build --release

# --- Runtime stage ---
FROM rust:1.84-slim

WORKDIR /app
# Copy only the compiled binary
COPY --from=builder /app/target/release/rusty-gates-server /app/rusty-gates-server
CMD ["./rusty-gates-server"]

# client/Dockerfile
# --- Builder stage ---
FROM rust:1.84 as builder

WORKDIR /app
COPY . .

# Build the binary
RUN cargo build --release

# --- Runtime stage ---
FROM rust:1.84-slim

# Install any dependencies here if needed
RUN apt-get update && \
    apt-get install -y vim # example: add what your client needs

# Copy the compiled binary from the builder stage
COPY --from=builder /app/target/release/rusty-gates-client /app/rusty-gates-client

# Optional: default command is a shell
CMD ["/bin/bash"]

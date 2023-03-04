FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && \
    apt-get install -y git cmake make g++

# Clone the zroxy project
RUN git clone https://github.com/0x7a657573/zroxy.git

# Build zroxy
WORKDIR /zroxy/build
RUN cmake .. && \
    make

# Copy the zroxy binary and configuration file to a new image
FROM ubuntu:22.04
COPY --from=0 /zroxy/build/zroxy /usr/local/bin/zroxy

#COPY zroxy.conf /

# Set the entrypoint
ENTRYPOINT ["/usr/local/bin/zroxy", "-c", "/zroxy.conf"]

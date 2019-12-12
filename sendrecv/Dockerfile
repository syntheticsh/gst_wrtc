FROM syntheticsh/gstreamer:1.16.2

RUN wget -O rustup.sh https://sh.rustup.rs && sh ./rustup.sh -y
ENV PATH=$PATH:/root/.cargo/bin/

RUN USER=root cargo new --bin gst-rust
WORKDIR /gst-rust

COPY Cargo.lock ./Cargo.lock
COPY Cargo.toml ./Cargo.toml

RUN cargo build
RUN rm src/*.rs

COPY ./src ./src
RUN touch ./src/main.rs && cargo build

CMD echo "Waiting a few seconds for you to open the browser at localhost:8080" \
    && sleep 10 \
    && /gst-rust/target/debug/gst-rust --peer-id=1 --server=ws://127.0.0.1:8443

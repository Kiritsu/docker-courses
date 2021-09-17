FROM debian:buster-slim AS precomp

RUN apt-get update -y && \
    apt-get install -y git build-essential && \
    git clone https://github.com/fanux/tetris.git && \
    cd tetris/src && \
    g++ --static -o game *cpp -lpthread && \
    mkdir /out && \
    cp game /out/

FROM busybox

COPY --from=precomp /out/game /bin

RUN chmod +x /bin/game

ENTRYPOINT sh -c "/bin/game"

FROM ibm-semeru-runtimes:open-11-jre-jammy
ENV MIRAI_VERSION 2.15.0
WORKDIR /mirai
RUN mkdir -p /mirai/libs &&\
curl -L https://maven.aliyun.com/repository/public/net/mamoe/mirai-core-all/$MIRAI_VERSION/mirai-core-all-$MIRAI_VERSION-all.jar -o /mirai/libs/mirai-core-all.jar &&\
curl -L https://maven.aliyun.com/repository/public/net/mamoe/mirai-console/$MIRAI_VERSION/mirai-console-$MIRAI_VERSION-all.jar -o /mirai/libs/mirai-console.jar &&\
curl -L https://maven.aliyun.com/repository/public/net/mamoe/mirai-console-terminal/$MIRAI_VERSION/mirai-console-terminal-$MIRAI_VERSION-all.jar -o /mirai/libs/mirai-console-terminal.jar &&\
mkdir -p /mirai/plugins &&\
curl -L https://ghproxy.com/https://github.com/cssxsh/fix-protocol-version/releases/download/v1.10.0/fix-protocol-version-1.10.0.mirai2.jar -o /mirai/plugins/fix-protocol-version.mirai2.jar &&\
curl -L https://ghproxy.com/https://github.com/KasukuSakura/mirai-login-solver-sakura/releases/download/v0.0.12/mirai-login-solver-sakura-0.0.12.mirai2.jar -o /mirai/plugins/mirai-login-solver-sakura.mirai2.jar
COPY ./run-0.1.0.jar /mirai/plugins/run.jar
COPY ./yiri-0.2.0.mirai2.jar /mirai/plugins/yiri.mirai2.jar
COPY ./start-mirai-console /mirai/start-mirai-console
RUN chmod +x /mirai/start-mirai-console && /mirai/start-mirai-console --no-console && rm /mirai/plugins/run.jar
CMD ["/mirai/start-mirai-console"]

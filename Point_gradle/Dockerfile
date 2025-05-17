# ベースイメージの指定
FROM openjdk:21-jdk

# 作業ディレクトリを設定します (一時的なビルド用)
WORKDIR /app

# アプリケーションのソースコードをコンテナにコピーします
COPY . /app/

# アプリケーションをビルドし、JAR ファイルを作成します
RUN javac -classpath /app/servlet-api.jar -d build/classes /app/src/main/java/**/*.java && \
    jar -cvf app.jar -C build/classes .

# アプリケーションのJARファイルをコピー
COPY app.jar /app/app.jar

# アプリケーションの起動コマンド
CMD ["java", "-jar", "/app/app.jar"]

# ポートを公開します
EXPOSE 8080

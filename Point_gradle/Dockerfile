# ベースイメージの指定
FROM openjdk:21-jdk

# 作業ディレクトリを設定します (一時的なビルド用)
WORKDIR /app

# アプリケーションのソースコードをコンテナにコピーします
COPY . /app/

# アプリケーションをビルドし、JAR ファイルを作成します
RUN javac -classpath /app/src/main/resources:/app/src/main/java -d build/classes /app/src/main/java/**/*.java && \
    jar -cvf app.jar -C build/classes .

# アプリケーションのJARファイルを指定の場所にコピー
# ここではCOPYは不要なので、CMDで直接実行する
# これにより、app.jarを直接実行します

# アプリケーションの起動コマンド
CMD ["java", "-jar", "app.jar"]

# ポートを公開します
EXPOSE 8080

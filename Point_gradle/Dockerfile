# ベースイメージの指定
FROM openjdk:21-jdk

# 作業ディレクトリを設定します
WORKDIR /app

# アプリケーションのソースコードをコンテナにコピーします
COPY . /app/

# Jakarta Servlet APIの依存関係を追加
RUN wget -q https://repo1.maven.org/maven2/jakarta/servlet/jakarta.servlet-api/5.0.0/jakarta.servlet-api-5.0.0.jar -P /app/libs/

# アプリケーションをビルドし、JAR ファイルを作成します
RUN javac -classpath /app/libs/jakarta.servlet-api-5.0.0.jar:/app/src/main/resources -d build/classes /app/src/main/java/**/*.java && \
    jar -cvf app.jar -C build/classes .

# アプリケーションの起動コマンド
CMD ["java", "-jar", "app.jar"]

# ポートを公開します
EXPOSE 8080

FROM eclipse-temurin:17-jdk
COPY Main.java /Main.java
RUN javac Main.java
CMD ["java", "Main"]

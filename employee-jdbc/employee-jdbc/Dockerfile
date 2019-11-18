#BASE IMAGE - BUILDER
FROM maven AS builder

#CREATE DIRECTORY

RUN mkdir -p /test

#COPY FILES
COPY . /test/

#SWITCH TO WORKING DIRECTORY
WORKDIR /test

#INSTALL DEPENDENCIES
RUN mvn clean install

RUN cd /test/target/ && ls

From openjdk:8
COPY --from=builder /test/target/employe-jdbc-0.0.1-SNAPSHOT.jar employee-jdbc-0.0.1-SNAPSHOT.jar
CMD ["java","-jar","employee-jdbc-0.0.1-SNAPSHOT.jar"]
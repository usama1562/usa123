FROM tomcat:9.0ss

# Set the working directory
WORKDIR /opt

# Set environment variables
ENV APP_HOME=/usr/local/tomcat
ENV PORT=8080

# Install necessary tools for downloading files
RUN apt-get update && apt-get install -y curl

# Download and place the WAR and JAR files
RUN curl -o $APP_HOME/webapps/student.war https://piyubucket.s3.amazonaws.com/student.war
RUN curl -o $APP_HOME/lib/mysql-connector.jar https://piyubucket.s3.amazonaws.com/mysql-connector.jar

# Copy the configuration files
COPY config /opt

# Modify the Tomcat configuration
RUN sed -i '20r /opt/config' $APP_HOME/conf/context.xml

# Expose the port
EXPOSE 8080

# Set the entry point to run Tomcat
CMD ["catalina.sh", "run"]

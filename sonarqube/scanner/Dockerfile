FROM gcc:latest

RUN apt update && apt full-upgrade -y

# Install compilation target
RUN apt install gcc-arm-none-eabi -y

# Install SonarQube Build Wrapper
WORKDIR /tmp
RUN wget https://sonarcloud.io/static/cpp/build-wrapper-linux-x86.zip
RUN unzip build-wrapper-linux-x86.zip -d /opt/
RUN rm build-wrapper-linux-x86.zip
RUN echo "export PATH=/opt/build-wrapper-linux-x86:\$PATH" >> ~/.profile

# Install SonarQube Scanner CLI
WORKDIR /tmp
RUN wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-6.2.1.4610-linux-x64.zip
RUN unzip sonar-scanner-cli-6.2.1.4610-linux-x64.zip -d /opt/
RUN rm sonar-scanner-cli-6.2.1.4610-linux-x64.zip
RUN echo "export PATH=/opt/sonar-scanner-6.2.1.4610-linux-x64/bin:\$PATH" >> ~/.profile

# Set default directory
WORKDIR /root/FreeRTOS-analyzed

# Enable symbolic links in the repository 
RUN 
RUN git submodule update --init --recursive

# Load the new environment variables
ENTRYPOINT ["bash"]
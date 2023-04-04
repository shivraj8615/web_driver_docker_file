# Step1 base image of ubuntu
FROM ubuntu
# making os interective
RUN apt update -y
WORKDIR app
COPY . /app/
# step2 install browser
RUN apt -f install -y
RUN apt-get install -y wget
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get install -y tzdata
RUN wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN apt-get install ./google-chrome-stable_current_amd64.deb -y
# step3 intall webdriver(selenium) for web scraping
ENV CHROMEDRIVER_VERSION 2.19
ENV CHROMEDRIVER_DIR /chromedriver
RUN mkdir $CHROMEDRIVER_DIR

# Download and install Chromedriver
RUN wget -q --continue -P $CHROMEDRIVER_DIR "http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip"
RUN apt-get install unzip
RUN unzip $CHROMEDRIVER_DIR/chromedriver* -d $CHROMEDRIVER_DIR/

# Put Chromedriver into the PATH
ENV PATH $CHROMEDRIVER_DIR:$PATH

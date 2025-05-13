# Use Python 3.12-slim base image
FROM python:3.12-slim

# Install dependencies
RUN apt-get update && \
    apt-get install -y git libssl-dev libffi-dev build-essential python3-dev wget krb5-user figlet ruby && \
    pip install --no-cache-dir pipx && \
    gem install lolcat
 
# Install Impacket
RUN pipx install impacket==0.12.0
 
# Install Netexec
#RUN pipx install netexec
RUN pipx ensurepath
RUN pipx install git+https://github.com/Pennyw0rth/NetExec
 
# Add the adshareenum script to the container
COPY adshareenum /usr/local/bin/adshareenum
RUN chmod +x /usr/local/bin/adshareenum

# Create output directory
RUN mkdir /output
 
# Entry command
ENTRYPOINT ["/usr/local/bin/adshareenum"]
 
 
# sudo docker build -t adshareenum .
# sudo docker run --rm -it -p 7070:7070 adshareenum  

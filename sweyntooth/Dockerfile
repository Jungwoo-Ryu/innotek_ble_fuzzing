FROM python:2.7.17-slim-buster
# Default script to execute
ENV test dhcheck_skip.py
ENV port /dev/ttyACM0
ENV addr ""
WORKDIR /
# Add main python scripts and folders
ADD *.py /
ADD drivers /drivers/
ADD libs /libs/ 
ADD extras /extras/
ADD captures /captures/
# Add helper files
ADD nRF52_driver_firmware.zip requirements.txt install_sweyntooth.sh flash_nRF52_driver_firmware.sh /
# --- FIX FOR DEBIAN BUSTER EOL ---
# Update apt repository URLs to the official archive
RUN sed -i 's/deb.debian.org/archive.debian.org/g' /etc/apt/sources.list && \
    sed -i 's/security.debian.org\/debian-security/archive.debian.org\/debian-security/g' /etc/apt/sources.list

# Install dependencies
RUN apt-get update -y && chmod +x install_sweyntooth.sh && ./install_sweyntooth.sh && pip install pyserial && apt-get autoremove -y && apt-get clean
CMD [ "sh", "-c", "python ${test} ${port} ${addr} && find ./ -maxdepth 1 -name '*.pcap' -exec cp {} logs \\; && find ./extras -maxdepth 1 -name '*.pcap' -exec cp '{}' logs  \\;" ]

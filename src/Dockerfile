FROM ghcr.io/pg9182/northstar-dedicated:1-tf2.0.11.0-ns1.9.3

# Go to tmp folder, download launcher files, extract them, copy, delete old folder
RUN cd /tmp && \
    mkdir rcon-pr-temp && \
    cd rcon-pr-temp && \
    wget https://nightly.link/R2Northstar/NorthstarLauncher/actions/artifacts/318200693.zip && \
    unzip *.zip && \
    sudo mv NorthstarLauncher.exe /usr/lib/northstar/NorthstarLauncher.exe && \
    sudo mv Northstar.dll /usr/lib/northstar/Northstar.dll && \
    cd .. && \
    rm -r rcon-pr-temp

# Port needed for RCON
EXPOSE 37015/tcp

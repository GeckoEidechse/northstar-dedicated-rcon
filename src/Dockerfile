FROM ghcr.io/pg9182/northstar-dedicated:1-tf2.0.11.0-ns1.9.4

# Go to tmp folder, download launcher files, extract them, copy, delete old folder
RUN cd /tmp && \
    mkdir rcon-pr-temp && \
    cd rcon-pr-temp && \
    wget https://nightly.link/R2Northstar/NorthstarLauncher/actions/runs/2870656032/NorthstarLauncher-efec6a0.zip && \
    unzip *.zip && \
    sudo mv NorthstarLauncher.exe /usr/lib/northstar/NorthstarLauncher.exe && \
    sudo mv Northstar.dll /usr/lib/northstar/Northstar.dll && \
    cd .. && \
    rm -r rcon-pr-temp

# Change mod version so that RCON enabled server is visible from outside as such
RUN \
    sudo sed -i -E 's/1\.9\.4/1\.9\.4-RCON/' /usr/lib/northstar/R2Northstar/mods/Northstar.Client/mod.json && \
    sudo sed -i -E 's/1\.9\.4/1\.9\.4-RCON/' /usr/lib/northstar/R2Northstar/mods/Northstar.Custom/mod.json && \
    sudo sed -i -E 's/1\.9\.4/1\.9\.4-RCON/' /usr/lib/northstar/R2Northstar/mods/Northstar.CustomServers/mod.json

# Port needed for RCON
EXPOSE 37015/tcp

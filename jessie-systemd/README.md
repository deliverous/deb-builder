# Jessie systemd

This container backport systemd from sid to jessie and add a package to have systemd-journal-gatewayd. To use it run : 
  
    docker build -t systemd .
    docker run systemd | tar -xv -C /output/directory/

Original patch was take from https://bugs.debian.org/742802, thanks Daniel Schaal

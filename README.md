
#Install apex and ords in docker db


`docker create -it --name 23cfree -p 8521:1521 -p 8500:5500 -p 8023:8080 -p 9043:8443 -p 9922:22 -e ORACLE_PWD=E container-registry.oracle.com/database/free:latest
curl -o unattended_install_23c.sh https://raw.githubusercontent.com/symekutz/23cOracleUnAttendedInstall/main/src/unattended_install_23c.sh
curl -o 00_start_installer.sh https://raw.githubusercontent.com/symekutz/23cOracleUnAttendedInstall/main/src/00_start_installer.sh
docker cp unattended_install_23c.sh 23cfree:/home/oracle
docker cp 00_start_installer.sh 23cfree:/opt/oracle/scripts/startup
docker start 23cfree`

`docker exec -it 23cfree /bin/bash
 tail -f /home/oracle/unattended_apex_install_23c.log`


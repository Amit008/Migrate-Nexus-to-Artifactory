Migrate-Nexus-to-Artifactory <br>
Steps of Migration: <br>
1. Script can be configured to download all or specific Repository <br>
2. Loop thorugh Folder structure locally on machine and upload downloaded Artifacts in Artifactory<br>
<br>
<br>
<br>

wget -r -np -nH –cut-dirs=3 -R index.html -R *sha1,*md5,*xml,*pom  -l0 http://<IPAddress>:<portNo>/nexus/content/repositories/ <br>
for file in `find /<RepositporyName>/* -type f` ; do  <br>
parentname="$(basename "$(dirname "$file")")"    <br>
###This will print the file which is going to be uploaded in nexus###<br>
echo "$parentname/$(basename "$file")";  <br>
curl -v -X PUT --user admin:password  --upload-file <PATH>/<RepositoryName>/$parentname/$(basename "$file")"; <br>
http://<Ipaddress>:<portNo>/artifactory/sample/$parentname/$(basename "$file")";  <br>
done

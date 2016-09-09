Migrate-Nexus-to-Artifactory
Step
1. Script can be configured to download all or specific Repository <br>
2. Loop thorugh Folder structure locally on machine and upload downloaded Artifacts in Artifactory<br>
<br>
<br>
<br>

wget -r -np -nH –cut-dirs=3 -R index.html -R *sha1,*md5,*xml,*pom  -l0 http://192.168.1.101:32769/nexus/content/repositories/
for file in `find /<RepositporyName>/* -type f` ; do
parentname="$(basename "$(dirname "$file")")"
###This will print the file which is going to be uploaded in nexus###
echo "$parentname/$(basename "$file")"; 
curl -v -X PUT --user admin:password  --upload-file <PATH>/<RepositoryName>/$parentname/$(basename "$file")";
http://<Ipaddress>:<portNo>/artifactory/sample/$parentname/$(basename "$file")"; 
done

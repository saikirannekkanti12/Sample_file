# ALL COMMANDS RUN INSIDE IN THE VM TRYING TO CONNECT APPLICATION INSIDE VM TO DB

# Installing google cloudsql inside in Virtual machine 
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy && chmod +x cloud_sql_proxy

# Connecting Database table through DB CREATE --> connection ----> create Table (user )
# SQL_CONNECTION_NAME , find in cloudSQL -- connection
export SQL_CONNECTION=[SQL_CONNECTION_NAME]

echo $SQL_CONNECTION

# To activate the proxy connection to your Cloud SQL database and send the process to the background, run the following command:
./cloud_sql_proxy -instances=$SQL_CONNECTION=tcp:3306 &

-----------------------------------------------------------------------------------------------------------------------
# Configure the Wordpress application. To find the external IP address of your virtual machine, query its metadata:
curl -H "Metadata-Flavor: Google" http://169.254.169.254/computeMetadata/v1/instance/network-interfaces/0/access-configs/0/external-ip && echo

Go to the wordpress-proxy external IP address in your browser and configure the Wordpress application.
Note: If you encounter the This site can’t be reached error, try accessing the site using http://ExternalIP





# install docker and run a sample container 
wget https://raw.githubusercontent.com/jaibwtl/automation/main/install-docker.sh
sh install-docker.sh

# install docker and run a sample container 
wget https://raw.githubusercontent.com/jaibwtl/automation/main/splunk-install-docker.sh
sh splunk-install-docker.sh
#wait for 2-3 min. 
#URL: http://PublicIP:8000 
#User: admin
#Password: Alpha#05082023


#honeycomb 
sudo apt install python3-pip
python3 -m pip install honeycomb-opentelemetry --pre
opentelemetry-bootstrap --action=install
python3 -m pip install Flask
wget https://raw.githubusercontent.com/jaibwtl/automation/main/myapp.py
export OTEL_SERVICE_NAME="mydemoapp"
export HONEYCOMB_API_KEY="-------update your own key --------------"
nohup opentelemetry-instrument python3 myapp.py &
cat nohup.out 
curl localhost:5000

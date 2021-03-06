ssh -i "~/Downloads/maximKEY.pem" ubuntu@ec2-54-87-240-215.compute-1.amazonaws.com

# Let's setup an env to work quickly
sudo apt install golang-go
git clone https://github.com/muesli/gitomatic.git

# Get the code 
ssh-keygen
git clone git@github.com:vatit-trustit-1/mensch-gateway.git

# Setup poor man's CD flow
./gitomatic/gitomatic -push=false -author "Max" -email "max@trustit.com" -interval "5s" mensch-gateway

# Let's get flask ready
sudo apt install python-is-python3
sudo apt install python3-venv
cd ~/mensch-gateway/
python3 -m venv venv
. venv/bin/activate
pip install Flask

# Run the app
export FLASK_APP=main.py
export FLASK_ENV=development
flask run --host=0.0.0.0

# Chrome Test
http://ec2-54-87-240-215.compute-1.amazonaws.com:5000 

> We're live.

# Now let's go create the github app...
App public page https://github.com/apps/mensch-trustit-2021

# Docker time

sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install docker-ce
sudo usermod -aG docker ${USER}
FROM cimg/python:3.8 AS base

# install node
RUN sudo apt-get update 

#&& sudo apt-get install -y \
#    software-properties-common \
#    npm

# install node
RUN sudo apt install -y nodejs

# install npm
RUN sudo apt install npm

# install yarn
RUN sudo npm install --global yarn

# show versions
RUN node --version && \
    yarn --version 

# Install ganache-cli
RUN sudo yarn global add ganache-cli

# Install pip
RUN sudo add-apt-repository universe && \
    sudo apt-get update && \
    sudo apt-get install python3-pip

# Install PIPX
RUN python3 -m pip install --user pipx && \
    python3 -m pip install --upgrade pip && \
    python3 -m pip install --user -U pipx && \
    python3 -m pipx ensurepath && \
    which pipx

# install brownie eth
RUN ~/.local/bin/pipx install eth-brownie && \
    echo `brownie --version`

# install numpy 
RUN ~/.local/pipx/venvs/eth-brownie/bin/python3 -m pip install numpy

# install openzeppelin
RUN sudo yarn global add @openzeppelin/contracts

# compile .sol to download EVM 0.8.11
RUN mkdir /tmp/brownietmp && \
    cd /tmp/brownietmp && \
    brownie init
COPY ./Dummy.sol /tmp/brownietmp/contracts
RUN cd /tmp/brownietmp && \
    brownie compile --all


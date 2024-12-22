FROM node

WORKDIR /workspace/dev/

RUN apt-get update && apt-get upgrade -y && \
  apt-get install git sudo -y && \
  apt-get clean

# installing neovim 
RUN curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz && \
  rm -rf /opt/nvim && \
  tar -C /opt -xzf nvim-linux64.tar.gz && \
  echo 'export PATH="$PATH:/opt/nvim-linux64/bin"' >> /home/node/.bashrc && \
  rm -rf nvim-linux64*

# instaling neovim config
RUN git clone https://github.com/pinugit/my-astrovim-config.git /home/node/.config/nvim

# installing starship
RUN curl -sS https://starship.rs/install.sh | sh -s -- --yes  && \
  echo 'eval "$(starship init bash)"' >> /home/node/.bashrc 

# Ensure proper ownership of the home directory
RUN chown -R node:node /home/node
RUN chown -R node:node /workspace/dev

USER node


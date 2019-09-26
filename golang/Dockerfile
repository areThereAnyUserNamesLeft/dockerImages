FROM golang:latest

RUN apt-get update && apt-get install -y htop \
        neovim \ 
        silversearcher-ag \
        fzf \
        xclip \
        xsel \ 
        zsh \
        curl \
        wget \ 
        zsh-syntax-highlighting

RUN mkdir -p /root/.local/share/nvim/site/autoload/
RUN mkdir -p /root/.config/
WORKDIR /root/.local/share/nvim/site/autoload/
RUN wget -O plug.vim https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
RUN curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
RUN sh -c "$(wget -O- https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

RUN chsh -s /bin/zsh root 
RUN rm /root/.zshrc
WORKDIR /root
RUN git init
RUN git remote add origin https://github.com/areThereAnyUserNamesLeft/dots.git 
RUN git fetch origin 
RUN git checkout docker  
RUN nvim --headless +'PluginInstall' +"qa"
  
WORKDIR /go



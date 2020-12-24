FROM hex/base

USER hex
WORKDIR /home/hex

RUN sudo apt-add-repository ppa:ondrej/php
RUN sudo apt-get update && sudo apt-get install -y php
# additional extensions for php
RUN sudo apt-get update && sudo apt-get install -y zip unzip php-zip php-curl php-mbstring php-xml

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --filename=composer #--install-dir=/usr/local/bin
RUN sudo mv composer /usr/local/bin
RUN php -r "unlink('composer-setup.php');"
RUN echo 'PATH=$PATH:~/.composer/vendor/bin' >> ~/.bashrc

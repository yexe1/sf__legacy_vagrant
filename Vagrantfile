Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-12.04"

  
  config.vm.network "private_network", ip: "192.168.56.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    # Установка PostgreSQL 8.4
    apt-get update -y
    apt-get install -y wget gnupg
    sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
    apt-get update -y
    apt-get install -y postgresql-8.4 postgresql-contrib-8.4
    service postgresql start
  SHELL
end

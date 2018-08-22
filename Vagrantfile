Vagrant.configure("2") do |config|

  # special base box for vm
  config.vm.box = "packer-centos7"
  
  # stop  check update for base box
  config.vm.box_check_update = false

  # define vm name "small-program" for cli show
  config.vm.define "small-program" do |sp|

    # special private ip
    sp.vm.network "private_network", ip: "192.168.33.10"

    # special share folder
    sp.vm.synced_folder "src/", "/srv/website"

    # special forward port
    # common opreation
    sp.vm.network "forwarded_port", guest: 80, host: 80
    sp.vm.network "forwarded_port", guest: 8080, host: 8080
    # special opreation
    # from below append " protocol: "tcp/udp" "

    # special shell script for init
    # this have two type optional
    # "inline" and "path"
    config.vm.provision "shell", path: "install-docker/install-docker.sh"

    # custome provider
    config.vm.provider "virtualbox" do |v|
      
      # special vm name for provider gui
      v.name = "small-program"

      # special memory
      v.memory = 800

    end	

  end

  # split line ###########################################

end

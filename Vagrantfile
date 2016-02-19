# -*- mode: ruby -*-
# vi: set ft=ruby :

# Specify Vagrant version and Vagrant API version
Vagrant.require_version ">= 1.6.0"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

Vagrant.configure(2) do | config |
  config.vm.synced_folder ".",   # Disable synced folders for the Docker container
    "/vagrant",                  # (prevents an NFS error on "vagrant up")
    disabled: true

  config.vm.provider "docker" do | docker |

    # Define the location of the Vagrantfile for the host VM
    # Comment out this line to use default host VM that is
    # based on boot2docker
    docker.vagrant_vagrantfile  = "host/Vagrantfile"
    docker.name                 = 'nginx-container'   # Specify a friendly name for the Docker container
    docker.image                = "nginx"             # Specify the Docker image to use
    docker.ports                = [                   # Specify port mappings, if omitted, no ports are mapped!
      '80:80',
      '443:443'
    ]
  end
end

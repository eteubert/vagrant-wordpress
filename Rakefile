require "vagrant"

task :setup do
  env = Vagrant::Environment.new
  raise "Must run `vagrant up`" if !env.primary_vm.created?
  raise "Must be running!" if !env.primary_vm.vm.running?
  
  env.primary_vm.ssh.execute do |ssh|
    ssh.exec! "export LC_ALL=en_US.UTF-8"
    ssh.exec! "git clone git://github.com/eteubert/dotfiles.git"
    ssh.exec! "sudo gem install rake"
    
    puts "\nNow do the following to finish the setup:"
    puts "vagrant ssh"
    puts "go to ~/dotfiles and type `rake install` to setup dotfiles"
    puts "sudo chsh -s /usr/bin/zsh vagrant"
    puts "sudo reboot"
  end  
end

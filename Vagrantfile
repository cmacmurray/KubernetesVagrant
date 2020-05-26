Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.5"

  config.vm.define "node1"
  config.vm.define "node2"
  config.vm.define "node3"
  config.vm.define "node4"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
    ansible.groups = {
      "EtcdServers" => ["node1"],
      "ControllerServers" => ["Controller1"],
      "WorkerServers" => ["Worker1","Worker2"],
      "all_groups:children" => ["group1", "group2"],
      "node1:vars" => {"IpAddress" => "172.16.33.101",
                      "NetMask" => "16",
                      "Gateway" => "172.16.33.1"}
    }
  end
end

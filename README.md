# README

    $ ansible-playbook -i hosts/vagrant setup.yml -e "@vars/test.yml"
    $ ansible-playbook -i hosts/production setup.yml -e "@vars/production.yml"
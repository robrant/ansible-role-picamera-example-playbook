

# About

Example playbook to show how to make calls to the ansible role that configures
a picamera for a Raspberry Pi.

# Dependencies

* I've only tested this on a Mac and Raspberry Pi B+ running Jessie (Dec 2016).
* You'll need Ansible on your local development machine/laptop.
* This repo uses a `git submodule` to pull in the role from [ansible-role-pi-camera](https://github.com/robrant/ansible-role-pi-camera).

# Usage

* Attach a picamera to the dedicated picamera interface on your Raspberry Pi.

* Clone this repo

      $> git clone https://github.com/robrant/ansible-role-picamera-example-playbook.git

* Get the submodule

      $> git submodule init

* Move some folders:

      $> cd ansible-role-picamera-example-playbook
      $> mv roles/picamera/library .
      $> mv roles/picamera/top_level_handlers roles

* Modify `playbook.yml` as you need:

        - hosts: pis
          roles:
            - picamera
          tags: picamera

* Modify `hosts` file as you need; replace `pibox0` with either the hostname or IP address of your pi.

* Run it

      $> ansible-playbook --user=pi --ask-pass -i hosts playbook.yml

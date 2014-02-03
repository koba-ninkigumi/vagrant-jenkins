# Jenkins on Ubuntu on Vagrant on Mac OS X

## 前準備

### ホストとなる Mac OS X で環境構築

#### 手動でインストール

0. VirtualBoxのインストール
	0. ダウンロードサイト: [Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads) 
0. Vagrantのインストール
	0. ダウンロードサイト: [Vagrant - www.vagrantup.com](http://www.vagrantup.com/)

#### Terminal上で作業

vagrantの各種プラグインとberkshelfをインストール

	vagrant plugin install sahara
	vagrant plugin install vagrant-vbguest
	vagrant plugin install vagrant-omnibus
	sudo gem i berkshelf

	vagrant box add ubuntu-amd64-13.10 http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box

## 仮想環境の構築

githubからVagrantfile, Berksfile, recipieなどをダウンロードする

	cd ~/Desktop/
	git-clone https://github.com/koba-ninkigumi/vagrant-jenkins.git
	cd vagrant-jenkins

仮想環境を起動する

	vagrant up

最後にWebブラウザでJenkinsにアクセスして動作チェックする

	http://192.168.33.10:8080/


# Jenkins on Ubuntu on Vagrant on Mac OS X

2014/2/3

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

##仮想環境を構築

	cd ~/Desktop
	mkdir vagrant-jenkins
	cd vagrant-jenkins

	vagrant box add ubuntu-amd64-13.10 http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box

### まずはJenkins環境を手動で構築してみる（この項は読み飛ばして良い）

#### Mac OS X上での作業

Vagrantfileを生成

	vagrant init

Vagrantfile を修正（修正内容は後ほど）

	nano Vagrantfile

仮想環境を起動する

	vagrant up

Vagrantの仮想環境にsshログイン

	vagrant ssh

#### Ubuntu上での作業

	wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
	sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
	sudo aptitude update
	sudo aptitude install -y jenkins

#### Mac OS X上での作業

最後にWebブラウザでJenkinsにアクセスして動作チェックする

	http://192.168.33.10:8080/


### 次にChef-Soloを利用した方法

#### Mac OS X上での作業

githubからVagrantfile, Berksfile, recipieなどをダウンロードする

	cd ~/Desktop/vagrant-jenkins
	git-clone
	cd xxxxx

仮想環境を起動する

	vagrant up

最後にWebブラウザでJenkinsにアクセスして動作チェックする

	http://192.168.33.10:8080/


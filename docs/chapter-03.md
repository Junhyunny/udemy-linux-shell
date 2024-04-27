
## Chapter 03

Vagrant CLI 도구를 사용해 가상 머신을 프로비저닝(provisioning)한다. Vagrant는 사용하기 쉽고, 가상 머신을 재구축하기 쉽다. 다양한 가상화 프로바이더 환경을 지원하지만, 이번 강의에선 VirtualBox에서 가상 머신을 프로비저닝하는데 사용한다. 

Vagrant에서 사용되는 컨셉들을 살펴보자. 박스(box)는 운영 체제를 의미한다. 다음 명령어를 통해 박스를 다운로드 받을 수 있다.

```
$ vagrant box add USER/BOX
```

예를 들어 다음 명령어를 실행하면 ubuntu 운영체제를 다운로드 받는다.

```
$ vagrant box add ubuntu/trusty64
```

프로젝트(project)는 vagrant 파일이 존재하는 폴더를 의미한다. 폴더 이름은 가상 머신 이름을 사용한다. `test-vm` 프로젝트를 만들어보자. 

- `test-vm` 디렉토리를 만든다.
- `test-vm` 디렉토리로 이동한다.
- vagrant 프로젝트를 초기화한다.

```
$ mkdir test-vm

$ cd test-vm

$ vagrant init ubuntu/trusty64
os7
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

Vagrant 명령어를 사용해 가상 머신을 실행해보자. VirtualBox에 박스가 이미 존재하는 경우 그대로 실행한다. 가상 머신은 headless 모드로 실행한다. headless 모드는 GUI 같은 사용자 인터페이스 환경이 없는 것을 의미한다.

```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'ubuntu/trusty64' version '20190514.0.0' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection reset. Retrying...
    default: 
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default: 
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default: 
    default: Guest Additions Version: 4.3.40
    default: VirtualBox Version: 7.0
==> default: Mounting shared folders...
    default: /vagrant => /Users/junhyunk/Desktop/workspace/udemy/udemy-linux-shell/examples/chapter-03/test-vm
```

다음과 같은 Vagrant 명령어들이 존재한다. 

```
$ vagrant halt [VM] # stops the VM
$ vagrant up [VM] # starts the VM
$ vagrant suspend [VM] # suspends the VM
$ vagrant resume [VM] # resumes the VM
$ vagrant destroy [VM] # removes the VM
```

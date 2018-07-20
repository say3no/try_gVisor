# try_gVisor

[gVisor](https://github.com/google/gvisor)をためしたり遊んだり速度比較したりしたい。

## 準備
2018/07/20時点では`x86_64 Linux 3.17+`でしか動かないためAWSのやっすいの借りたよ。

```bash
sudo yum update -y
sudo yum install docker
sudo systemctl start docker

wget https://storage.googleapis.com/gvisor/releases/nightly/latest/runsc
wget https://storage.googleapis.com/gvisor/releases/nightly/latest/runsc.sha512
sha512sum -c runsc.sha512
chmod +x runsc
sudo mv runsc /usr/local/bin

git clone https://github.com/say3no/try_gVisor
cp try_gVisor/daemon.json /etc/docker/.

sudo usermod -g docker ec2-user
exit
```

usergroupの反映とかで一度`exit`が必要不可欠

## runscなしの場合
コンテナの内側からコンテナが乗っている船の情報が見えるのかどうかを検証する。


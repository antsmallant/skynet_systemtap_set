## 安装 stap 的依赖

```
sudo apt update

sudo apt install -y systemtap systemtap-runtime linux-headers-$(uname -r) build-essential elfutils dwarves

sudo apt install -y systemtap-sdt-dev

sudo apt install -y ubuntu-dbgsym-keyring || true
echo "deb http://ddebs.ubuntu.com $(lsb_release -cs) main restricted universe multiverse" | sudo tee /etc/apt/sources.list.d/ddebs.list
echo "deb http://ddebs.ubuntu.com $(lsb_release -cs)-updates main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list.d/ddebs.list
echo "deb http://ddebs.ubuntu.com $(lsb_release -cs)-security main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list.d/ddebs.list
sudo apt update
# 下面这个包名因内核构建方式可能不同，两个都试试哪一个存在
sudo apt install -y linux-image-$(uname -r)-dbgsym || sudo apt install -y linux-image-unsigned-$(uname -r)-dbgsym

```

## 自检

```
stap -v -e 'probe begin { printf("hello SystemTap\n"); exit() }'
```
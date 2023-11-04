# Avail Light Node Rehber



# Minimum Sistem Gereksinimleri

* 2 CPU
* 4GB RAM
* 20-40GB SSD
* Ubuntu 20.04 ya da üstü

# Kurulum

Sistemi güncelleyelim.

```
sudo apt update && sudo apt upgrade -y
```
Gerekli paketleri yükleyelim.

```
sudo apt install make clang pkg-config libssl-dev build-essential git screen protobuf-compiler -y
```
Rust kuralım ve ayarlayalım.

```
curl https://sh.rustup.rs -sSf | sh
```
```
source $HOME/.cargo/env
```
```
rustup update nightly
```
```
rustup target add wasm32-unknown-unknown --toolchain nightly
```
Avail Light reposunu klonlayalım.

```
git clone https://github.com/availproject/avail-light.git
```
Screen oluşturalım ve Avail klasörüne girelim.

```
screen -S avail-light
```
```
cd avail-light
```

1.7.2 sürümünün branchını hedefleyelim.

```
git checkout v1.7.2
```

Kurulumu yapalım.

```
cargo build --release
```

Kurulumun bitmesini bekleyelim. Şimdi servis dosyası oluşturacağız.

```
sudo touch /etc/systemd/system/avail-lightd.service
```
```
sudo nano /etc/systemd/system/avail-lightd.service
```
Aşağıdaki kodları yapıştırıp CTRL + X 'e ve ardından Y'ye basarak kaydedip çıkıyoruz.

```
[Unit] 
Description=Avail Light Client
After=network.target
StartLimitIntervalSec=0
[Service] 
User=root 
ExecStart= /root/avail-light/target/release/avail-light --network biryani
Restart=always 
RestartSec=120
[Install] 
WantedBy=multi-user.target
```

Servis dosyasını aktifleştirelim ve başlatalım.

```
sudo systemctl enable avail-lightd.service
```
```
sudo systemctl start availd-lightd.service
```
```
sudo systemctl status avail-lightd.service
```
Servisin çalıştığını gördükten sonra tekrar Ctrl + C ile servis infosunu kapatalım. Ardından light node loglarını açalım.

```
journalctl -f -u avail-lightd
```
İşlemler bu kadar. Screenden çıkabiliriz.

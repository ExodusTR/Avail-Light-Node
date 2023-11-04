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
screen -S avail
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


# Spheron

Shpheron Network'ün Fizz Node'unu kurdum, bir süredir test ediyorum sorunsuz bir şekilde puan kazanıyorum gördüğünüz gibi.

Ekran Resmi 2024-10-04 22 19 25  
Donanım olarak 4 vCPU 8 RAM bir sunucu kullandım.

Kurulumu hatırladığım kadarıyla yazıyorum 3 gün önce kurdum net aklımda değil her step, zaten kolay yaparsınız siz.

## Kurulum  
1. Buradan cüzdanınızı bağlıyorsunuz.  
2. Sonra ilerlemeniz gereken bir kaç step var, onları tamamlayıp node kurulum sayfasına geçiyorsunuz.  
3. Sonra lokasyonunuza yakın olan (sunucu lokasyonu) bir provider seçiniz ve görseldeki setup kısmına geliniz.  

Ekran Resmi 2024-10-04 22 29 00  
Setup dosyasını indirip sunucunuzun içine atınız (WinSCP gibi bir program ile veya Termius).

## Komutlar  
Aşağıdaki komutları tek tek girelim:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo systemctl enable docker

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo fallocate -l 4096M /swapfile

sudo chmod 600 /swapfile

sudo mkswap /swapfile

sudo swapon /swapfile
```

## Dosya izinlerini verelim
```bash
chmod +x /root/fizzup.sh
```

## Yeni bir ekran başlatalım
```bash
screen -S fizz
```

## Node başlatmak için iki komuttan birisini kullanabilirsiniz
```bash
bash /root/fizzup.sh
sh /root/fizzup.sh
```

## Log kontrolü için komut
```bash
docker compose -f ~/.spheron/fizz/docker-compose.yml logs -f
```

@ruesandora'dan alıntıdır.

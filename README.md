<h1 align="center">CrossFi Testnet Kurulumu
### Lava Node testini kuruyoruz. Sağ üstten yıldızlayıp forklamayı unutmayalım. Sorularınız olursa: <a href="https://t.me/CoinHuntersTR/34102" target="_blank" rel="Coin Hunters TR" >Coin Hunters TR</a>

![lava-network-testnet-rehberi](https://user-images.githubusercontent.com/111747226/220886500-561d6199-3c6d-4af3-8a45-b003ac7768ba.png)

## Sistem gereksinimleri:
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| CrossFi | 4          | 8         | 160  |


## 1) Güncellemeleri Yapıyoruz.

```
sudo apt update && sudo apt upgrade -y
```

## 2) Otomatik script çalıştırıp sizden istenen cüzdan adı ve Validator ismini giriyorsunuz.
> Port yerine, değişiklik yapmayacaksanız 26 yazıp enter yapmanız yeterli.
```
wget -q -O crossfi.sh https://raw.githubusercontent.com/CoinHuntersTR/CrossFi/main/crossfi.sh && chmod +x crossfi.sh && ./crossfi.sh
```

  


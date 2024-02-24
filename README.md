<h1 align="center">CrossFi Testnet Kurulumu
  

![lava-network-testnet-rehberi](https://pbs.twimg.com/profile_banners/1681767569823334401/1698851466/1500x500)

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

  


<h1 align="center">CrossFi Testnet Kurulumu
  
<br/><br>
![lava-network-testnet-rehberi](https://pbs.twimg.com/profile_banners/1681767569823334401/1698851466/1500x500)

## Sistem gereksinimleri:
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| CrossFi | 4          | 8         | 160  |


## 1) Kurulum
```
sudo apt update && sudo apt upgrade -y
```

### Otomatik script çalıştırıp sizden istenen cüzdan ve Validator ismini giriyorsunuz.

> Port yerinde, değişiklik yapmanıza gerekyok,  26 yazıp enter yapmanız yeterli.

```
wget -q -O crossfi.sh https://raw.githubusercontent.com/CoinHuntersTR/CrossFi/main/crossfi.sh && chmod +x crossfi.sh && ./crossfi.sh
```

###  Test cüzdanını ekleme

> Burada, Başvuru yaparken veya maille token istediğiniz cüzdanı, node içine aktaracağız.

> `cüzdanismi` yerine oto scriptte verdiğiniz ismi verin.

> Cüzdanı açarken aldığınız kelimeleri girin.

> Sizden şifre belirlemenizi isteyecek şifre belirleyin. Test cüzdanınıza node üzeriden açmış olacaksınız.

```
crossfid keys add cüzdanismi --recover
```

### Senkronizasyon Kontrolü

![Ekran görüntüsü 2024-02-25 004315](https://github.com/CoinHuntersTR/Babylon-Testnet3/assets/111747226/16dd6048-6700-4bf4-b6d7-fd037f5331f0)

> Komut sonrasında `false` çıktısı aldığınızda Validator kurulumuna geçebilirsiniz.

```
crossfid status 2>&1 | jq .SyncInfo
```

## 2) Validator Çalıştırma

> `moniker` yazan yere tırnaklar içinde Validator isminizi yazıyoruz.

> `details` yazan yere tırnaklar içinde istediğiniz bir şey yazabilirsiniz.

>  `website` yazan yere twitter yada github linkinizi ekleyebilirsiniz.


```
crossfid tx staking create-validator \
--amount 9000000000000000000000mpx \
--from $WALLET \
--commission-rate 0.1 \
--commission-max-rate 0.2 \
--commission-max-change-rate 0.01 \
--min-self-delegation 1 \
--pubkey $(crossfid tendermint show-validator) \
--moniker "" \
--website "" \
--details "CoinHunters Community" \
--chain-id crossfi-evm-testnet-1 \
--gas auto --gas-adjustment 1.5 --gas-prices 10000000000000mpx \
-y
```

### Kendi Validatorüne Token delege etme

> `cüzdanismi` yerine kendi verdiğiniz ismi yazmanız gerekiyor.

> 1MPX = 1000000000000000000mpx  yapıyor, yani 18 tane 0 var. Ona göre cüzdanınızdan, kendi validatörünüze delege edebilirsiniz.

```
crossfid tx staking delegate $(crossfid keys show cüzdanismi --bech val -a) 9000000000000000000000mpx --from cüzdanismi --chain-id crossfi-evm-testnet-1 --gas-adjustment 1.5 --gas auto --gas-prices 10000000000000mpx -y
```
### Explorer

> [BURADAN](https://testnet.itrocket.net/crossfi) explorer ulaşarak, blok sayısını ve kendi validatorünüzü görebilirsiniz.

## 3) Yedek Alma

> Sunucuna bir şey oldu. Hetzner kapattı. Yada yanlışlıkla sildiniz. Size lazım olan dosyayı yedekledikten sonra sorun yok.

> Nasıl yedekliyoruz? Cosmos projelerinde bir tane dosyayı bilgisayarınıza indirdiğinizde işlem tamamdır.  `priv_validator_key.json` dosyasını indirmemiz gerekiyor.

> Bunun için winscp veya mobaxterm kullanabilirsiniz.

> Dosya yolu bu şekildedir;  `/root/.mineplex-chain/config/priv_validator_key.json` bu dosyayı bir yere kayıt etmeyi unutmayın.


## 4) Validator Bilgilerini Güncelleme

> Buradaki bilgileri güncelleyerek Validator Adınızı ve diğer değişiklikleri yapabilirsiniz.

```
crossfid tx staking edit-validator \
--new-moniker "YOUR_MONIKER_NAME" \
--identity "YOUR_KEYBASE_ID" \
--details "YOUR_DETAILS" \
--website "YOUR_WEBSITE_URL" \
--chain-id crossfi-evm-testnet-1 \
--commission-max-change-rate 0.01 \
--from cüzdanismi \
--gas auto --gas-adjustment 1.5 --gas-prices 10000000000000mpx \
-y
```
### Validatore Resim ekleme;

> [BURADAN](https://keybase.io/) keybase sitesine gidin, kayıt olup resminizi yükleyip adımları takip edin. size `F0F603C1097C160F` benzer ifade verecek, onu `identity` ID olarak eklerseniz validator resminiz görünür.


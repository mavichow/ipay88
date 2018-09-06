# IPay88
[![Build Status](https://img.shields.io/packagist/dt/karyamedia/ipay88.svg?maxAge=2592000)](https://packagist.org/packages/karyamedia/ipay88)

Ipay88 payment gateway module.

**NOTE**: Your require to request demo account from techsupport@ipay88.com.my

## Installation

I've make this project available to install via [Composer](https://getcomposer.org/) with following command:

```bash
$ composer require karyamedia/ipay88 dev-master
```

## Example Controller

```php
<?php

class Payment {

    protected $_merchantCode;
    protected $_merchantKey;

    public function __construct()
    {
        parent::__construct();
        $this->_merchantCode = 'xxxxxx'; //MerchantCode confidential
        $this->_merchantKey = 'xxxxxxxxx'; //MerchantKey confidential
    }

    public function index()
    {
        $request = new IPay88\Payment\Request($this->_merchantKey);
        $this->_data = array(
            'merchantCode' => $request->setMerchantCode($this->_merchantCode),
            'paymentId' =>  $request->setPaymentId(1),
            'refNo' => $request->setRefNo('EXAMPLE0001'),
            'amount' => $request->setAmount('0.50'),
            'currency' => $request->setCurrency('MYR'),
            'prodDesc' => $request->setProdDesc('Testing'),
            'userName' => $request->setUserName('Your name'),
            'userEmail' => $request->setUserEmail('email@example.com'),
            'userContact' => $request->setUserContact('0123456789'),
            'remark' => $request->setRemark('Some remarks here..'),
            'lang' => $request->setLang('UTF-8'),
            'signature' => $request->getSignature(),
            'responseUrl' => $request->setResponseUrl('http://example.com/response'),
            'backendUrl' => $request->setBackendUrl('http://example.com/backend')
            );

        IPay88\Payment\Request::make($this->_merchantKey, $this->_data);
    }
    
    public function response()
    {   
        $response['Remark']       = $_REQUEST["Remark"];
        $response['MerchantCode'] = $_REQUEST["MerchantCode"];
        $response['PaymentId']    = $_REQUEST["PaymentId"];
        $response['RefNo']        = $_REQUEST["RefNo"];
        $response['Amount']       = $_REQUEST["Amount"];
        $response['Currency']     = $_REQUEST["Currency"];
        $response['Remark']       = $_REQUEST["Remark"];
        $response['TransId']      = $_REQUEST["TransId"];
        $response['AuthCode']     = $_REQUEST["AuthCode"];
        $response['Status']       = $_REQUEST["Status"];
        $response['ErrDesc']      = $_REQUEST["ErrDesc"];
        $response['Signature']    = $_REQUEST["Signature"];
        $response['CCName']       = $_REQUEST["CCName"];
        $response['CCNo']         = $_REQUEST["CCNo"];
        $response['S_bankname']   = $_REQUEST["S_bankname"];
        $response['S_country']    = $_REQUEST["S_country"];
        print_r($response);die;
    }
}
```

## Credits

[Leow Kah Thong](https://github.com/ktleow)

[Fikri Marhan](https://github.com/fikri-marhan)

[Pijoe](https://github.com/pijoe86)

[aa6my](https://github.com/aa6my)

## Reference
https://github.com/cchitsiang/ipay88

https://github.com/fastsafety/ipay88

## Lisence

MIT © [Karyamedia](https://github.com/karyamedia/karya). Please see [License File](LICENSE.md) for more information.

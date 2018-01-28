# wxpay
    微信统一下单
## Sample
**sample.php**
```php
include 'wechatAppPay.class.php';
//1.统一下单方法
$wechatAppPay = new wechatAppPay($appid, $mch_id, $notify_url, $key);
$params['body'] = '商品描述'; //商品描述
$params['out_trade_no'] = 'O20160617021323-001'; //自定义的订单号
$params['total_fee'] = '100'; //订单金额 只能为整数 单位为分
$params['trade_type'] = 'APP'; //交易类型 JSAPI | NATIVE | APP | WAP 
$result = $wechatAppPay->unifiedOrder( $params );
print_r($result); // result中就是返回的各种信息信息，成功的情况下也包含很重要的prepay_id
//2.创建APP端预支付参数
/** @var TYPE_NAME $result */
$data = @$wechatAppPay->getAppPayParams( $result['prepay_id'] );
// 根据上行取得的支付参数请求支付即可
print_r($data);
# wechat-pay-app
    微信APP支付-服务器端PHP SDK 
    精简的SDK代码,方便程序扩展使用
    官方文档说明: https://pay.weixin.qq.com/wiki/doc/api/app/app.php?chapter=9_1
    微信APP支付流程: 服务器端下单 -> 生成预支付参数 -> APP通过预支付调起客户端支付
# 使用示例
### 生成APP支付参数示例代码
```php
//初始化配置参数
$options = array(
     'appid'=>'wx8888888888888888',//填写微信分配的公众账号ID
     'mch_id'=>'1900000109',//填写微信支付分配的商户号
     'notify_url'=>'http://www.baidu.com/',//填写微信支付结果回调地址
     'key'=>'5K8264ILTKC'//填写微信商户支付密钥
);

//创建示例对象
$WechatAppPay = new wechatAppPay($options); 

//设置下单参数
$params['body'] = '商品描述';//商品描述
$params['out_trade_no'] = '1217752501201407';	//自定义的订单号
$params['total_fee'] = '100';	//订单金额 只能为整数 单位为分
$params['trade_type'] = 'APP';	//交易类型 JSAPI | NATIVE |APP | WAP 

//请求微信【统一下单】接口,成功会返回 预支付交易会话标识 prepay_id
$result = $wechatAppPay->unifiedOrder( $params );

//生成APP端调起支付所需的参数
$data = $wechatAppPay->getAppPayParams( $result['prepay_id'] );
```

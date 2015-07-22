# wechat-pay-app
微信APP支付-服务器端PHP SDK
 *	$options = array(
 *		'appid' 	=> 	'wx8888888888888888',		//填写微信分配的公众账号ID
 *		'mch_id'	=>	'1900000109',				    //填写微信支付分配的商户号
 *		'notify_url'=>	'http://www.baidu.com/',	//填写微信支付结果回调地址
 *		'key'		=>	'5K8264ILTKC'				//填写微信商户支付密钥
 *	);
 *	统一下单方法
 *	$WechatAppPay = new wechatAppPay($options);
 *	$params['body'] = '商品描述';						//商品描述
 *	$params['out_trade_no'] = '1217752501201407';	//自定义的订单号
 *	$params['total_fee'] = '100';					//订单金额 只能为整数 单位为分
 *	$params['trade_type'] = 'APP';					//交易类型 JSAPI | NATIVE |APP | WAP 
 *	$result = $wechatAppPay->unifiedOrder( $params );
 
 
 * //创建APP端预支付参数
 * $data = $wechatAppPay->getAppPayParams( $result['prepay_id'] );

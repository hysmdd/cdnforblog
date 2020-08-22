---
layout: false
---
<!DOCTYPE html>
<html>
<head>
	<style>
		text-align: center;
		width: 100%;
		margin-top: 50px;
	</style>
</head>
<body>
<div id="reward">
  
<div>您的喜欢是作者写作最大的动力！❤️</div>

<div class="reward">
  <a href="https://github.com/Kaiyuan/donate-page" target="_blank" class=" tr3" title="Github"><span
      id="github"></span></a>
  <ul id="RewardBox" class="list pos-f tr3">
    
    
    <li id="AliPayOR" title="支付宝打赏">AliPay</li>
    
    
    <li id="WeChatPayOR" title="微信打赏">WeChatPay</li>
    
    
    <li id="QQPayOR" title="QQ打赏">QQPay</li>
    
  </ul>
  <div id="RewardText" class="tr3">Donate</div>
  <div id="QRBox" class="pos-f left-100">
    <div id="MainBox"></div>
  </div>
</div>
</div>
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-2.0.3.min.js"></script>
<script>
  jQuery(document).ready(function () {
    var QRBox = $('#QRBox');
    var MainBox = $('#MainBox');
    var AliPayOR = 'https://www.zhengyuanyuan520.cn/images/Alipay.png';
    var WeChatPayOR = 'https://www.zhengyuanyuan520.cn/images/Wechat.png';
    var QQPayOR = 'https://www.zhengyuanyuan520.cn/images/QQPay.png';

    function showQR(QR) {
      if (QR) {
        MainBox.css('background-image', 'url(' + QR + ')');
      }
      $('#RewardText,#RewardBox,#github').addClass('blur');
      QRBox.fadeIn(300, function (argument) {
        MainBox.addClass('showQR');
      });
    }

    $('#RewardBox>li').click(function (event) {
      var thisID = $(this).attr('id');
      if (thisID === 'AliPayOR') {
        showQR(AliPayOR);
      } else if (thisID === 'WeChatPayOR') {
        showQR(WeChatPayOR);
      } else if (thisID === 'QQPayOR') {
        showQR(QQPayOR);
      }
    });

    MainBox.click(function (event) {
      MainBox.removeClass('showQR').addClass('hideQR');
      setTimeout(function (a) {
        QRBox.fadeOut(300, function (argument) {
          MainBox.removeClass('hideQR');
        });
        $('#RewardText,#RewardBox,#github').removeClass('blur');
      }, 600);

    });
  });
</script>
</body>
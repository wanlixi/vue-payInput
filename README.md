# vue-payInput
### 2017-11-30 Create by wanlixin

基于vue2.0开的一个类似微信支付密码输入的组件
### 效果如下：
![](https://github.com/wanlixi/vue-payInput/blob/master/imitation-pay-input.gif)
#### 功能描述
<ol>
  <li>仅支持输入数字且仅6位</li>
  <li>输入字符不可见</li>
  <li>输入密码完毕自动隐藏键盘</li>
</ol>

#### 实现思路
<ol>
  <li>先循环出来6个小方格</li>
  <li>同位置放一个同大小的input输入框（其实不同位置，不同大小也可以；如果考虑字母数字混合输入可以使用的password类型）</li>
  <li>input type="number"</li>
  <li>利用vue里面 watch 检测输入框内容的长度，处理到6个小方格里面  </li>
  <li>隐藏的小黑圆点，采用before伪类实现，减少DOM</li>
</ol>

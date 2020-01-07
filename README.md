# Project1-4_Smart_contract #
### Version 1.0 ###
A smart contract which can be used in a transaction between a single buyer and a single seller.<br/>
There are 4 roles: contract provider, buyer, seller and logistics.<br/>
Every role has its own function access authorizations. <br/>
### Version 2.0 : Concurrent multi-transaction ###
Now the trading platform which is constructed with a smart contract has supported multi-transaction.<br/>
When a contractProvider set a array which includes 3 addresses as parameters of function createTransaction(address[]), a new transaction will be created and the 3 parameters will be regarded as buyer address, seller address and logistics company address respectively (according to the sequence you give).<br/>
If the function createTransaction(address[]) is called by a conctractProvider successfully, a new transaction will be created and it will not effect other transactions which already exist. 

<br>
<br>

# 系統流程 #

![img](https://github.com/cislab-yzu/Project1-4_Smart_contract/blob/master/smart%20concract%20step/1-4-1.png)

1.由Contract Provider決定誰是買家，誰是賣家和誰是物流公司(setBuyer(address),setSeller(address),setLogistics(address))<br/><br/>
2.賣家與物流分別有權限設定商品價格與物流費用(setCommodityPrice(uint),setDeliveryFee(uint))<br/><br/>
3.買家可以查看物流費用(showDeliveryFee()),和商品費用(showCommodityPrice())<br/><br/>
4.買家需要依據查詢到的金額分別支付物流費用（payLogistics(uint))和支付商品費用(payCommidity(uint))，這些錢先暫時存在合約中<br/><br/>
5.賣家可以確認發貨(delivering())，物流公司可以確認貨物已送達(delivered())，並從合約中領取到物流費用<br/><br/>
6.買家確認商品沒問題後，選擇(receivingComfirm())確認收貨，合約中剩餘的貨款將轉賬到賣家賬戶<br/><br/>
7.交易完成

# CampaignService
CampaignServiceは、キャンペーンの操作を提供します。

#### WSDL
| environment | url |
|---|---|
| production  | https://location.im.yahooapis.jp/services/Vx.x/CampaignService?wsdl |
| sandbox  | https://sandbox.im.yahooapis.jp/services/Vx.x/CampaignService?wsdl |

#### Namespace
http://im.yahooapis.jp/V6

#### サービス概要
キャンペーンの操作を提供します。

#### 操作
CampaignServiceで提供される操作を説明します。

## get
### リクエスト
キャンペーン情報を取得します。

| パラメータ | 必須 | データ型 | 説明 | 
|---|---|---|---|
| selector | ○ | [CampaignSelector](../data/CampaignSelector.md) | getメソッドの検索条件（実行パラメータ）を保持します。 | 

##### ＜リクエストサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Header>
    <ns1:RequestHeader>
      <ns1:license>1111-1111-1111-1111</ns1:license>
      <ns1:apiAccountId>2222-2222-2222-2222</ns1:apiAccountId>
      <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
    </ns1:RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:get>
      <ns1:selector>
        <ns1:accountId>1111111111</ns1:accountId>
        <ns1:campaignIds>1111111110</ns1:campaignIds>
        <ns1:campaignIds>2222222220</ns1:campaignIds>
        <ns1:userStatus>ACTIVE</ns1:userStatus>
        <ns1:userStatus>PAUSED</ns1:userStatus>               
        <ns1:paging>
          <ns1:startIndex>1</ns1:startIndex>
          <ns1:numberResults>20</ns1:numberResults>
        </ns1:paging>
        <ns1:campaignType>APP</ns1:campaignType>
      </ns1:selector>
    </ns1:get>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| パラメータ | データ型 | 説明 | 
|---|---|---|
| rval | [CampaignPage](../data/CampaignPage.md) | getメソッドの実行結果（全Entityのリスト）を保持します。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>CampaignService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>1</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:getResponse>
            <ns1:rval>
                <ns1:Page.Type>CampaignPage</ns1:Page.Type>
                <ns1:totalNumEntries>2</ns1:totalNumEntries>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:campaignId>1000000001</ns1:campaignId>
                        <ns1:campaignName>campaign name1</ns1:campaignName>
                        <ns1:userStatus>PAUSED</ns1:userStatus>
                        <ns1:servingStatus>PENDING</ns1:servingStatus>
                        <ns1:startDate>20101201</ns1:startDate>
                        <ns1:endDate>20371231</ns1:endDate>
                        <ns1:budget>
                            <ns1:amount>10000000</ns1:amount>
                            <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                            <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>INTEREST_MATCH</ns1:adProductType>
<!-- フリークエンシを設定していない場合はfrequencyCapはエレメントなし -->
<!-- コンバージョン最適化設定無効状態。 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:campaignId>1000000002</ns1:campaignId>
                        <ns1:campaignName>campaign name2</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20371231</ns1:endDate>
                        <ns1:budget>
                            <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                            <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
                        <ns1:frequencyCap>
                            <ns1:level>AD_GROUP</ns1:level>
                            <ns1:timeUnit>MONTH</ns1:timeUnit>
                            <ns1:impression>15</ns1:impression>
                        </ns1:frequencyCap>
<!-- コンバージョン最適化設定無効状態。 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                   <ns1:operationSucceeded>true</ns1:operationSucceeded>
                      <ns1:campaign>
                         <ns1:accountId>1000000001</ns1:accountId>
                         <ns1:campaignId>1000000003</ns1:campaignId>
                         <ns1:campaignName>campaign name3</ns1:campaignName>
                         <ns1:userStatus>ACTIVE</ns1:userStatus>
                         <ns1:servingStatus>SERVING</ns1:servingStatus>
                         <ns1:startDate>20170316</ns1:startDate>
                         <ns1:endDate>20371231</ns1:endDate>
                         <ns1:budget>
                            <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                         </ns1:budget>
                         <ns1:biddingStrategy xsi:type="ns1:ManualCPV">
                            <ns1:type>MANUAL_CPV</ns1:type>
                         </ns1:biddingStrategy>
                         <ns1:adProductType>VIDEO_AD</ns1:adProductType>
                        <ns1:appName>app Name</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                      </ns1:campaign>
                </ns1:values>
            </ns1:rval>
        </ns1:getResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(ADD)
### リクエスト
キャンペーン情報を追加します。

| パラメータ | 必須 | データ型 | 説明 | 
|---|---|---|---|
| operations | ○ | [CampaignOperation](../data/CampaignOperation.md) | mutateメソッドで操作対象となるキャンペーン情報を保持します。 | 

##### ＜リクエストサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
     <ns1:RequestHeader>
          <ns1:license>1111-1111-1111-1111</ns1:license>
          <ns1:apiAccountId>2222-2222-2222-2222</ns1:apiAccountId>
          <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
      </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutate>
            <ns1:operations>
                <ns1:operator>ADD</ns1:operator>
                <ns1:accountId>100000001</ns1:accountId>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignName>Sample campaign1</ns1:campaignName>
                    <ns1:userStatus>PAUSED</ns1:userStatus>
                    <ns1:startDate>20101201</ns1:startDate>
                    <ns1:endDate>20101231</ns1:endDate>
                    <ns1:budget>
                        <ns1:amount>10000</ns1:amount>
                        <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                    </ns1:budget>
                    <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                        <ns1:type>MANUAL_CPC</ns1:type>
                    </ns1:biddingStrategy>
                    <ns1:adProductType>INTEREST_MATCH</ns1:adProductType>
                    <ns1:campaignType>STANDARD</ns1:campaignType>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignName>Sample campaign2</ns1:campaignName>
                    <ns1:userStatus>ACTIVE</ns1:userStatus>
                    <ns1:startDate>20121201</ns1:startDate>
                    <ns1:endDate>20121231</ns1:endDate>
                    <ns1:budget>
                        <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                    </ns1:budget>
                    <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                        <ns1:type>MANUAL_CPC</ns1:type>
                    </ns1:biddingStrategy>
                    <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
                    <ns1:frequencyCap>
                        <ns1:level>AD_GROUP</ns1:level>
                        <ns1:timeUnit>MONTH</ns1:timeUnit>
                        <ns1:impression>15</ns1:impression>
                    </ns1:frequencyCap>
                    <ns1:appName>app Name1</ns1:appName>
                    <ns1:campaignType>APP</ns1:campaignType>
                    <ns1:appId>1000000004</ns1:appId>
                    <ns1:appOs>IOS</ns1:appOs>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignName>Sample campaign3</ns1:campaignName>
                    <ns1:userStatus>ACTIVE</ns1:userStatus>
                    <ns1:startDate>20121201</ns1:startDate>
                    <ns1:endDate>20121231</ns1:endDate>
                    <ns1:budget>
                        <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                    </ns1:budget>
                    <ns1:biddingStrategy xsi:type="ns1:ManualCPV">
                        <ns1:type>MANUAL_CPV</ns1:type>
                    </ns1:biddingStrategy>
                    <ns1:adProductType>VIDEO_AD</ns1:adProductType>
                    <ns1:appName>app Name2</ns1:appName>
                    <ns1:campaignType>APP</ns1:campaignType>
                    <ns1:appId>sample.app.package</ns1:appId>
                    <ns1:appOs>ANDROID</ns1:appOs>
                </ns1:operand>
            </ns1:operations>
        </ns1:mutate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| パラメータ | データ型 | 説明 | 
|---|---|---|
| rval | [CampaignReturnValue](../data/CampaignReturnValue.md) | mutateメソッドの実行結果（全Entityのリスト）を保持します。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>CampaignService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>2</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutateResponse>
            <ns1:rval>
                <ns1:ListReturnValue.Type>CampaignReturnValue</ns1:ListReturnValue.Type>
                <ns1:Operation.Type>ADD</ns1:Operation.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000001</ns1:campaignId>
                        <ns1:campaignName>Sample campaign1</ns1:campaignName>
                        <ns1:userStatus>PAUSED</ns1:userStatus>
                        <ns1:servingStatus>PENDING</ns1:servingStatus>
                        <ns1:startDate>20101201</ns1:startDate>
                        <ns1:endDate>20101231</ns1:endDate>
                        <ns1:budget>
                            <ns1:amount>10000</ns1:amount>
                            <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                            <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>INTEREST_MATCH</ns1:adProductType>
<!-- コンバージョン最適化設定無効状態。 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:campaignType>STANDARD</ns1:campaignType>
                   </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000002</ns1:campaignId>
                        <ns1:campaignName>Sample campaign2</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20121231</ns1:endDate>
                        <ns1:budget>
                            <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
                        <ns1:frequencyCap>
                            <ns1:level>AD_GROUP</ns1:level>
                            <ns1:timeUnit>MONTH</ns1:timeUnit>
                            <ns1:impression>15</ns1:impression>
                        </ns1:frequencyCap>
<!-- コンバージョン最適化設定無効状態。 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name1</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000003</ns1:campaignId>
                        <ns1:campaignName>Sample campaign3</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20121231</ns1:endDate>
                        <ns1:budget>
                            <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPV">
                           <ns1:type>MANUAL_CPV</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>VIDEO_AD</ns1:adProductType>
                        <ns1:appName>app Name2</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>sample.app.package</ns1:appId>
                        <ns1:appOs>ANDROID</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
            </ns1:rval>
        </ns1:mutateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(SET)
### リクエスト
キャンペーン情報を更新します。

| パラメータ | 必須 | データ型 | 説明 | 
|---|---|---|---|
| operations | ○ | [CampaignOperation](../data/CampaignOperation.md) | mutateメソッドで操作対象となるキャンペーン情報を保持します。 | 

##### ＜リクエストサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>1111-1111-1111-1111</ns1:license>
            <ns1:apiAccountId>2222-2222-2222-2222</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutate>
            <ns1:operations>
                <ns1:operator>SET</ns1:operator>
                <ns1:accountId>100000001</ns1:accountId>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000001</ns1:campaignId>
                    <ns1:campaignName>Modify sample campaign001</ns1:campaignName>
                    <ns1:userStatus>ACTIVE</ns1:userStatus>
                    <ns1:startDate>20130101</ns1:startDate>
                    <ns1:endDate>20131231</ns1:endDate>
                    <ns1:budget>
                        <ns1:amount>1000000</ns1:amount>
                        <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                    </ns1:budget>
                    <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                         <ns1:type>MANUAL_CPC</ns1:type>
                    </ns1:biddingStrategy>
<!-- フリークエンシ設定リクエストが無ければ変更なし -->
<!-- コンバージョン最適化設定を有効にする場合はtargetCpaに1以上9999999999までの値を設定 -->
                    <ns1:conversionOptimizer>
                        <ns1:targetCpa>30</ns1:targetCpa>
                    </ns1:conversionOptimizer>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000002</ns1:campaignId>
                    <ns1:campaignName>Modify sample campaign002</ns1:campaignName>
<!-- フリークエンシ設定追加時はすべての項目をリクエスト -->
                    <ns1:frequencyCap>
                        <ns1:level>CAMPAIGN</ns1:level>
                        <ns1:timeUnit>WEEK</ns1:timeUnit>
                        <ns1:impression>5</ns1:impression>
                    </ns1:frequencyCap>
<!-- コンバージョン最適化設定を無効にする場合はtargetCpaに0を設定 -->
                    <ns1:conversionOptimizer>
                        <ns1:targetCpa>0</ns1:targetCpa>
                    </ns1:conversionOptimizer>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000003</ns1:campaignId>
                    <ns1:campaignName>Modify sample campaign002</ns1:campaignName>
<!-- フリークエンシ設定変更時は変更したい項目のみでリクエスト可能 -->
                    <ns1:frequencyCap>
                        <ns1:impression>8</ns1:impression>
                    </ns1:frequencyCap>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000004</ns1:campaignId>
                    <ns1:campaignName>Modify sample campaign002</ns1:campaignName>
<!-- ０指定でフリークエンシ設定解除 -->
                    <ns1:frequencyCap>
                        <ns1:impression>0</ns1:impression>
                    </ns1:frequencyCap>
                </ns1:operand>
            </ns1:operations>
        </ns1:mutate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| パラメータ | データ型 | 説明 | 
|---|---|---|
| rval | [CampaignReturnValue](../data/CampaignReturnValue.md) | mutateメソッドの実行結果（全Entityのリスト）を保持します。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>CampaignService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>2</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutateResponse>
            <ns1:rval>
                <ns1:ListReturnValue.Type>CampaignReturnValue</ns1:ListReturnValue.Type>
                <ns1:Operation.Type>SET</ns1:Operation.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>100000001</ns1:accountId>
                        <ns1:campaignId>100000001</ns1:campaignId>
                        <ns1:campaignName>Modify sample campaign001</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>PENDING</ns1:servingStatus>
                        <ns1:startDate>20130101</ns1:startDate>
                        <ns1:endDate>20131231</ns1:endDate>
                        <ns1:budget>
                           <ns1:amount>1000000</ns1:amount>
                           <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>INTEREST_MATCH</ns1:adProductType>
<!-- コンバージョン最適化設定有効状態。eligibilityFlg=ENABLEなのでtargetCpaが設定可能 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>30</ns1:targetCpa>
                            <ns1:eligibilityFlg>ENABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:campaignType>STANDARD</ns1:campaignType>
                   </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>100000001</ns1:accountId>
                        <ns1:campaignId>100000002</ns1:campaignId>
                        <ns1:campaignName>Modify sample campaign002</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20121231</ns1:endDate>
                        <ns1:budget>
                           <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
<!-- フリークエンシを設定していない場合はfrequencyCapはエレメントなし -->
<!-- コンバージョン最適化設定無効状態。eligibilityFlg=ENABLEなのでtargetCpaが設定可能 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>ENABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:campaignType>STANDARD</ns1:campaignType>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>100000001</ns1:accountId>
                        <ns1:campaignId>100000003</ns1:campaignId>
                        <ns1:campaignName>Modify sample campaign003</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20130601</ns1:startDate>
                        <ns1:endDate>20131231</ns1:endDate>
                        <ns1:budget>
                           <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
                        <ns1:frequencyCap>
                            <ns1:level>AD_GROUP</ns1:level>
                            <ns1:timeUnit>MONTH</ns1:timeUnit>
                            <ns1:impression>15</ns1:impression>
                        </ns1:frequencyCap>
<!-- コンバージョン最適化設定有効状態。eligibilityFlg=DISABLEだが、targetCpaの更新可能。一度0に更新すると設定不可。 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>30</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name1</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>100000001</ns1:accountId>
                        <ns1:campaignId>100000004</ns1:campaignId>
                        <ns1:campaignName>Modify sample campaign004</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20130601</ns1:startDate>
                        <ns1:endDate>20131231</ns1:endDate>
                        <ns1:budget>
                           <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
<!-- コンバージョン最適化設定無効状態。eligibilityFlg=DISABLEかつtargetCpa=0(無効)なのでtargetCpa設定不可 -->
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>DISABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name2</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>sample.app.package</ns1:appId>
                        <ns1:appOs>ANDROID</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
            </ns1:rval>
        </ns1:mutateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(REMOVE)
### リクエスト
キャンペーン情報を削除します。

| パラメータ | 必須 | データ型 | 説明 | 
|---|---|---|---|
| operations | ○ | [CampaignOperation](../data/CampaignOperation.md) | mutateメソッドで操作対象となるキャンペーン情報を保持します。 | 

##### ＜リクエストサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>1111-1111-1111-1111</ns1:license>
            <ns1:apiAccountId>2222-2222-2222-2222</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutate>
            <ns1:operations>
                <ns1:operator>REMOVE</ns1:operator>
                <ns1:accountId>100000001</ns1:accountId>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000001</ns1:campaignId>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000002</ns1:campaignId>
                </ns1:operand>
                <ns1:operand>
                    <ns1:accountId>100000001</ns1:accountId>
                    <ns1:campaignId>100000003</ns1:campaignId>
                </ns1:operand>
            </ns1:operations>
        </ns1:mutate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| パラメータ | データ型 | 説明 | 
|---|---|---|
| rval | [CampaignReturnValue](../data/CampaignReturnValue.md) | mutateメソッドの実行結果（全Entityのリスト）を保持します。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>CampaignService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>2</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutateResponse>
            <ns1:rval>
                <ns1:ListReturnValue.Type>CampaignReturnValue</ns1:ListReturnValue.Type>
                <ns1:Operation.Type>REMOVE</ns1:Operation.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000001</ns1:campaignId>
                        <ns1:campaignName>Sample campaign1</ns1:campaignName>
                        <ns1:userStatus>PAUSED</ns1:userStatus>
                        <ns1:servingStatus>PENDING</ns1:servingStatus>
                        <ns1:startDate>20101201</ns1:startDate>
                        <ns1:endDate>20101231</ns1:endDate>
                        <ns1:budget>
                            <ns1:amount>10000</ns1:amount>
                            <ns1:deliveryMethod>STANDARD</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                            <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>INTEREST_MATCH</ns1:adProductType>
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>30</ns1:targetCpa>
                            <ns1:eligibilityFlg>ENABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:campaignType>STANDARD</ns1:campaignType>
                   </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000002</ns1:campaignId>
                        <ns1:campaignName>Sample campaign2</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20121231</ns1:endDate>
                        <ns1:budget>
                           <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPC">
                           <ns1:type>MANUAL_CPC</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>TARGET_MATCH</ns1:adProductType>
                        <ns1:frequencyCap>
                            <ns1:level>AD_GROUP</ns1:level>
                            <ns1:timeUnit>MONTH</ns1:timeUnit>
                            <ns1:impression>15</ns1:impression>
                        </ns1:frequencyCap>
                        <ns1:conversionOptimizer>
                            <ns1:targetCpa>0</ns1:targetCpa>
                            <ns1:eligibilityFlg>ENABLE</ns1:eligibilityFlg>
                        </ns1:conversionOptimizer>
                        <ns1:appName>app Name1</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>1000000004</ns1:appId>
                        <ns1:appOs>IOS</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:campaign>
                        <ns1:accountId>1111111111</ns1:accountId>
                        <ns1:campaignId>100000003</ns1:campaignId>
                        <ns1:campaignName>Sample campaign3</ns1:campaignName>
                        <ns1:userStatus>ACTIVE</ns1:userStatus>
                        <ns1:servingStatus>SERVING</ns1:servingStatus>
                        <ns1:startDate>20120601</ns1:startDate>
                        <ns1:endDate>20121231</ns1:endDate>
                        <ns1:budget>
                           <ns1:deliveryMethod>ACCELERATED</ns1:deliveryMethod>
                        </ns1:budget>
                        <ns1:biddingStrategy xsi:type="ns1:ManualCPV">
                           <ns1:type>MANUAL_CPV</ns1:type>
                        </ns1:biddingStrategy>
                        <ns1:adProductType>VIDEO_AD</ns1:adProductType>
                        <ns1:appName>app Name2</ns1:appName>
                        <ns1:campaignType>APP</ns1:campaignType>
                        <ns1:appId>sample.app.package</ns1:appId>
                        <ns1:appOs>ANDROID</ns1:appOs>
                    </ns1:campaign>
                </ns1:values>
            </ns1:rval>
        </ns1:mutateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>

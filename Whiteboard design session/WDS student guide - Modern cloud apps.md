<!--
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Modern cloud apps
</div>

<div class="MCWHeader2">
 Whiteboard design session student guide
</div>

<div class="MCWHeader3">
March 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

# Modern cloud apps whiteboard design session student guide

## Abstract and learning objectives

In this whiteboard design session, you will work with a group to design a solution to modernize CSLA's e-commerce and back-end services, while maintaining existing PCI compliance. To ensure compliance, you will ensure data privacy and protection across all aspects of the system, in transit and at rest. The goal is to use Azure PaaS services for the public-facing and back-end websites, while providing a way for the on-premises components to securely communicate with these services. You will also design fault-tolerance and a regional failover plan of the Azure components.

By the end of this whiteboard design session, you will have a better understanding of how to modernize a legacy web app by retargeting it for the cloud, taking advantage of the many services Azure provides to enhance functionality and secure your solution's components by following best practices for PCI compliance and security.

## Step 1: Review the customer case study

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions: With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1. Meet your table participants and trainer.

2. Read all the directions for steps 1-3 in the student guide.

3. As a table team, review the following customer case study.

### Customer situation

The Contoso Sports League Association (CSLA) is one of the largest sports franchises. They have over 100 championships in their history and a huge, passionate fan base. They run a highly successful e-commerce website that sells merchandise to their legions of sports fans. The website is built using ASP.NET Core and currently hosted in a co-location.

They accept payment by credit card and owing to their high annual volume (in the tens of millions, processing about 50K per day) of transactions, need to ensure that they are Payment Card Industry Data Security Standards (PCI DSS) Level 1 compliant. Their website hosts the shopping cart and checkout process, but they defer the credit card authorization and capture responsibilities of the credit card processing to a third-party payment gateway. This payment gateway provides a web application programming interface (API) that is invoked over Transport Layer Security (TLS) from Contoso server-side logic. The call includes the credit card holder data (name, number, and so on) and returns a status indicating a success or failure in authorizing and capturing payment against the credit card. It is called after the customer clicks checkout, as a part of processing the order. They currently store their customer and profile data in SQL Server 2014.

In addition to the public facing e-commerce website, they have a backend website that supports their call center. Call center employees use this admin website to view customer orders. Customers can call in to the call center to place orders and pay for orders with their credit cards by phone.

CSLA manages the order fulfillment process. When an order arrives, they store the order details in their SQL database, and send a message for each order to their inventory management system running the warehouse. CSLA experiences a roughly 12-hour window that spans east to west coast business hours, during which they get most of their orders. The warehouse receives the message (which simply contains the order ID from the database), pulls up the order details identified in the message (by a lookup against the database), and then for each item in the order queues up a separate process to locate the item in inventory or place an order for it with their supplier. Once this initial status for each item in the order is collected, the inventory status is updated in the database and a confirmation email is sent to the customer indicating the estimated delivery date of their completed order (and if any items are in backorder). This inventory lookup rarely takes more than a few hours and never more than a day.

They have reached a point where managing their server infrastructure is becoming a real challenge. Contoso wants to understand more about platform as a service (PaaS) solutions. They wonder if PaaS could help them focus their efforts more on the core business value rather than infrastructure. They have observed that Azure has received PCI compliance certification and are interested in moving their solution to Azure. "We're finding that with every upgrade, we're spending more and more engineering time on infrastructure and less on the experience that matters most to our fan base," says Miles Strom, Chief Executive Officer (CEO) of Contoso Sports League Association, "we need to rebalance those efforts."

One example is in how they manage the usernames and passwords for call center operators and support staff, as applied to the call center admin website. Today they have a homegrown solution that stores usernames and passwords in the same database used for storing merchandise information. They have experimented with other third-party solutions in the past, and their employees found it jarring to see another company's logo displayed when logging into their own call center website. In creating their identity solution, they want to ensure they can brand the login screens with their own logo. Additionally, Contoso is concerned about hackers from foreign countries/regions gaining access to the administrator site. Before they choose an identity solution, they would like to see how it indicates such attempts.

There is one architectural enhancement Contoso would like to make in the transition to a PaaS solution. When a visitor loads the home page, it gets the list of featured products on offer (consisting of the product image, title, and URL) from the Offers service. The home page does it using a client-side GET request against an ASP.NET Web API service that is executed as the page loads in the browser. Contoso anticipates growing the functionality of this service and would like to scale it independently of the website.

Contoso is also looking to augment their data analytics story by introducing a data warehouse to enable them to analyze their historical data over time, particularly as their number of transactions soars in the cloud. They would like to plan for a solution that moves the data from their OLTP database into their data warehouse on a nightly basis, ideally with the minimum amount of infrastructure or development effort.

### Customer needs

1. Make architectural decisions that help to minimize engineering around infrastructure in favor of those that deliver core business value. Contoso is interested in understanding more about PaaS solutions.

2. Maintain existing PCI compliance.

3. Ensure data privacy and protection across all aspects of the system, in transit and at rest.

4. They want to be able to scale their offers' API independently of the website.

5. Ensure that they retain their core functionality, even if the way it is accomplished under the covers might change.

6. Provide a better solution for the management of usernames and passwords.

7. Provide a regional database failover plan that will enable the customer to initiate the failover to another region, allowing their various web applications and other hosted services to roll over to a synchronized database at minimal cost.

8. A data warehouse for analyzing their transaction history.

### Customer objections

1. It is not clear to us from the Azure Trust Center just how Azure helps our solution become PCI compliant.

2. Can we provide a solution that scales to meet our public demand, but is also secure for use by our call center and warehouse?

3. Our PCI compliance requires us to have a quarterly audit and to conduct occasional penetration tests. Is it supported by Azure?

4. Can we audit the Azure data center?

5. In the past, we have relied on SOASTA CloudTest to design and execute our web load tests at scale. In moving to Azure, are we still take advantage of CloudTest?

6. Our previous infrastructure did not have great performance monitoring of our websites. What options would you recommend we investigate that would work with our web apps in Azure?

7. We have heard that Azure's data warehouse can be paused. Does that mean we must store all our data in Azure Storage first before we can pause the instances and risk losing our data?

8. We know it's possible to use Azure SQL Database as our data warehouse. What should we consider when deciding between this and Azure Synapse Analytics?

### Infographic for common scenarios

![This diagram is of a Common scenario for an E-Commerce Website. The diagram begins with an end user, includes a services tier, internet tier, and data tier, and ends at an Enterprise. The diagram also includes Microsoft Azure, and Azure Virtual Network.](media/image2.png 'Common scenario for an E-Commerce Website')

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions:  With all participants at your table, answer the following questions and list the answers on a flip chart:

1. Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2. What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

*High-level architecture*

1. Without getting into the details, the following sections will address the details, diagram your initial vision for handling the top-level requirements for the e-commerce website, call center website, and inventory lookup process. You will refine this diagram as you proceed.

*Order fulfillment*

1. How would you recommend CSLA manage the inventory lookup queues? How would you help CSLA decide between Azure Queues and Service Bus? Be sure to consider details implied by CSLA's requirements such as volume, message lifetime, and sizing. Explain the details of any computations you make.

*Notifications*

1. How would you recommend CSLA manage notifying customers as their order in the CSLA orders database is processed? Are there specific Azure services that can be used? Include details on how this would be implemented and integrated into the proposed solution for CSLA.

*Offers service*

1. Would you propose Contoso use the Azure App Service API app to meet their requirements for the Offers service?

2. If so, what specific configurations would you need to make to support your proposed topology? Specifically, how would you implement the changes and configurations required to allow for inter-app communication between the e-commerce application and the Offers service?

*Geo-resiliency*

1. How would you implement high availability for the orders database to guard against regional data center outages? Be specific on how you would configure SQL Database and Azure Storage.

2. What process would you recommend to the customer to failover in the event of an outage, ensuring their web applications and associated Azure services change over to a secondary region?

3. How long would a failover take and how much data could be lost, in terms of time?

*Access control*

1. With respect to managing access to the call center website, explain how you would recommend Contoso implement a solution that meets their requirements. Be specific about both the implementation and the process you would use to gain Contoso's acceptance of the proposed solution.

*Enabling PCI compliance*

1. Keeping only the e-commerce website and handling of cardholder data in scope for PCI, consider the following in your design:

    - Are web apps deployed in Azure App Service Environments an option?

    - Explain how using Azure App Service Environments could address the PCI requirements.

    - Keeping in mind the best choice for securing inbound and outbound traffic for an App Service Environment, detail all inbound and outbound traffic for this solution that allows it to be PCI compliant and allows it to operate within Azure. It should include traffic into and out of the solution, outbound for the e-commerce website, and any other traffic between the apps within the solution.

    - Make sure to describe in detail the network topology you are using.

    - For any inbound and outbound application communications you are securing, please detail the specific mechanisms you will use to do so.

    - If your approach includes configuration scripts, please provide an example of the scripts.

2. Would you recommend they use Azure virtual machines? Why or why not?

*Data warehouse*

1. How would you recommend Contoso implement their data warehouse?

2. How would Contoso schedule nightly data transfers from their OLTP database to their data warehouse?

**Prepare**

Directions: With all participants at your table:

1. Identify any customer needs that are not addressed with the proposed solution.

2. Identify the benefits of your solution.

3. Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

1. Pair with another table.

2. One table is the Microsoft team and the other table is the customer.

3. The Microsoft team presents their proposed solution to the customer.

4. The customer makes one of the objections from the list of objections.

5. The Microsoft team responds to the objection.

6. The customer team gives feedback to the Microsoft team.

7. Tables switch roles and repeat Steps 2-6.

## Wrap-up

Timeframe: 15 minutes

Directions: Tables reconvene with the larger group to hear the facilitator/SME share the preferred solution for the case study.

## Additional references

| Description                                                  | Links        |
| :------------------------------------------------------------ | :--------------------------------- |
| Compliance Commitments                                       |                              <http://azure.microsoft.com/en-us/support/trust-center/services/>                              |
| Azure App Services                                           |                 <https://azure.microsoft.com/en-us/documentation/articles/app-service-value-prop-what-is/>                  |
| Azure Service Environment (ASE)                              |            <https://azure.microsoft.com/en-us/documentation/articles/app-service-app-service-environment-intro/>            |
| Integrate ILB ASE with Azure Application Gateway             |             <https://docs.microsoft.com/en-us/azure/app-service/environment/integrate-with-application-gateway>             |
| Configuring ASE Network Security Groups                      |            <https://docs.microsoft.com/en-us/azure/app-service/environment/network-info#network-security-groups>            |
| Geo Distributed Scale with ASE                               | <https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-geo-distributed-scale>  |
| Azure Trust Center                                           |                                  <http://azure.microsoft.com/en-us/support/trust-center/>                                   |
| Azure PCI Attestation of Compliance                          |   <http://download.microsoft.com/download/7/1/E/71E02A19-D1A4-448F-8CEA-D6A19398ABDA/Azure%20PCI%20AOC%20Feb%202015.pdf>    |
| PCI DSS v3.0                                                 |                               <https://www.pcisecuritystandards.org/documents/PCI_DSS_v3.pdf>                               |
| Azure Data Factory                                           | <https://azure.microsoft.com/en-us/documentation/articles/data-factory-data-movement-activities/#data-factory-copy-wizard/> |
| Azure SQL Database                                           |                <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-geo-replication-overview/>                 |
| Designing highly available services using Azure SQL Database |     <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-designing-cloud-solutions-for-disaster-recovery>      |
| SQL Database auto-failover groups | <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auto-failover-group?tabs=azure-powershell> |

-->
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')


<div class="MCWHeader1">
最新のクラウド アプリ
</div>

<div class="MCWHeader2">
 ホワイトボード設計セッション生徒用ガイド
</div>

<div class="MCWHeader3">
2020 年 3 月
</div>

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。著作権法による制限に関係なく、マイクロソフトの書面による許可なしに、このドキュメントの一部または全部を複製したり、検索システムに保存または登録したり、別の形式に変換したりすることは、手段、目的を問わず禁じられています。ここでいう手段とは、複写や記録など、電子的、または物理的なすべての手段を含みます。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

© 2019 Microsoft Corporation. All rights reserved.

Microsoft および <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> (英語) に掲載されているその他の商標は、マイクロソフト グループ各社の商標です。その他すべての商標は、その所有者に帰属します。


**目次**

<!-- TOC -->

- [最新のクラウド アプリホワイトボード設計セッション生徒用ガイド](#最新のクラウド-アプリホワイトボード設計セッション生徒用ガイド)
  - [要約と学習目標](#要約と学習目標)
  - [ステップ 1: 顧客事例の確認](#ステップ-1:-顧客事例の確認)
    - [顧客の状況](#顧客の状況)
    - [顧客のニーズ](#顧客のニーズ)
    - [顧客の反論](#顧客の反論)
    - [一般的なシナリオのインフォグラフィック](#一般的なシナリオのインフォグラフィック)
  - [ステップ 2: 概念実証ソリューションの設計](#ステップ-2:-概念実証ソリューションの設計)
  - [ステップ 3: ソリューションのプレゼンテーション](#ステップ-3:-ソリューションのプレゼンテーション)
  - [まとめ](#まとめ)
  - [参考資料](#参考資料)

<!-- /TOC -->

# 最新のクラウド アプリホワイトボード設計セッション生徒用ガイド<a name="最新のクラウド-アプリホワイトボード設計セッション生徒用ガイド"></a>

## 要約と学習目標<a name="要約と学習目標"></a>

このホワイトボード設計セッションでは、CSLA の eコマース サービスとバックエンド サービスを刷新したソリューションをグループで設計します。ソリューションは、変更前と同様に PCI に準拠するものとします。コンプライアンスを遵守するため、システム全体で通信中と格納中のどちらの状態のデータもプライバシーを守り、保護する必要があります。目標は、外部に公開する Web サイトとバックエンド Web サイトに Azure PaaS サービスを使用すること、およびオンプレミス コンポーネントとこれらのサービスの間に安全な通信方法を実装することです。また、フォールト トレランスでリージョン内のフェールオーバーに対応した Azure コンポーネントを設計することが求められます。

このホワイトボード設計セッションを修了すると、レガシ Web アプリをクラウド向けに刷新する方法、および各種 Azure サービスを利用してソリューションのコンポーネントの機能や安全性を強化する方法を、PCI 準拠やセキュリティのベスト プラクティスに従いながら習得できます。

## ステップ 1: 顧客事例の確認<a name="ステップ-1:-顧客事例の確認"></a>

**成果**

顧客のニーズを分析する。

時間: 15 分

指示: セッション参加者全員が集まり、進行役または SME が顧客事例の概要と技術的なヒントを提示します。

1. 自班の参加者とトレーナーが集まります。

2. 生徒用ガイドのステップ 1 ～ 3 の指示をすべて読みます。

3. 班全体で下記の顧客事例を確認します。

### 顧客の状況<a name="顧客の状況"></a>

Contoso Sports League Association (CSLA) は大手スポーツ フランチャイズで、これまでに 100 以上の選手権を開催しており、熱心なファンが非常に多く存在します。同社が運用する eコマース Web サイトも好調で、かなりの数のスポーツ ファンが商品を購入しています。サイトは ASP.NET Core で構築されていて、現在はコロケーションでホストされています。

このサイトはクレジット カード払いに対応しており、年間トランザクション数が膨大であるため (年間数千万件、1 日あたり約 5 万件)、Payment Card Industry Data Security Standards (PCI DSS) Level 1 に準拠する必要があります。この Web サイトではショッピング カートと精算処理をホストしていますが、クレジット カード処理の認証と取得はサードパーティの支払いゲートウェイに任せています。この支払いゲートウェイでは Web アプリケーション インターフェイス (API) が提供され、Contoso のサーバー側スクリプトから Transport Layer Security (TLS) を通じて呼び出すことができます。呼び出しにはクレジット カード所有者のデータ (氏名や番号など) が含まれ、クレジット カードの認証や支払い請求が成功したか失敗したかを示す状態が返されます。また、顧客がチェックアウトをクリックした後に注文処理の一部として呼び出されます。現在、顧客データやプロファイル データは SQL Server 2014 に格納されています。

外部に公開する eコマース Web サイト以外に、コール センターをサポートするバックエンド Web サイトも存在します。コール センター担当者は、この管理 Web サイトで顧客からの注文を表示しています。またコール センターでは、顧客からの電話で注文を受けたりクレジット カードでの支払いに対応したりしています。

CSLA では、注文調達プロセスを管理しています。注文を受けると、その詳細を SQL Database に格納し、倉庫の運用に使用される在庫管理システムに各注文のメッセージを送信します。CSLA の営業時間は米国東部から西部まで約 12 時間におよび、注文のほとんどはその間に発生します。データベースから倉庫に送られるメッセージには、注文 ID のみが含まれます。倉庫ではメッセージの注文 ID を基にデータベースを検索して注文の詳細を取得し、注文の各アイテムを個別のプロセスとしてキューに入れ、アイテムを在庫から探したり供給元に発注したりします。注文の各アイテムの初期状態が収集されたら、データベースの在庫状態が更新され、完了した注文の配送予定日 (および入荷待ちアイテムの有無) を含む確認メールが顧客に送信されます。在庫の検索はほとんどの場合数時間程度で完了し、1 日以上かかることはありません。

Contoso では、サーバー インフラストラクチャの管理負荷が深刻な問題となっています。また、サービスとしてのプラットフォーム (PaaS) ソリューションについて理解を深めたいと考えています。同社では、PaaS ソリューションがインフラストラクチャのために割く労力を軽減し、重要なビジネス価値の提供に集中するために役立つかどうかを検討しており、Azure が PCI コンプライアンス認定を受けていることを知って、自社ソリューションを Azure に移行することに興味を示しています。Contoso Sports League Association 最高経営責任者 (CEO) の Miles Strom 氏は次のように述べています。「アップグレードのたびにインフラストラクチャのエンジニアリングに要する時間が増えて、ファンの皆様への影響が大きいエクスペリエンスにかける時間が減っていることがわかりました。このバランスを改めなければなりません」

その例の 1 つが、Azure をコール センター管理 Web サイトに導入した場合にコール センター担当者やサポート スタッフのユーザー名とパスワードを管理する方法です。現在は自社開発ソリューションを使用しており、ユーザー名とパスワードは商品情報が格納されているものと同じデータベースに保存されています。過去にはサードパーティのソリューションを試したこともありましたが、コール センター管理 Web サイトにログインするときに他社のロゴが表示されるのが煩わしく感じられました。新たに作成する ID ソリューションでは、自社のロゴをあしらった独自デザインのログイン画面を使用したいと考えています。また、外国や他地域のハッカーから管理サイトに侵入されるリスクについても憂慮しており、ID ソリューションを選定する前に、このような攻撃がどのように示されるかを確認したいと考えています。

Contoso は、PaaS ソリューションへの移行にあたってアーキテクチャを強化したい点があります。ユーザーがホーム ページを読み込んだときに、Offers サービスが推薦する注目商品 (商品画像、見出し、URL を含む) のリストを取得するようにします。ブラウザーにホーム ページが読み込まれると、クライアントから ASP.NET Web API サービスへの GET 要求が実行され、注目商品が取得されます。このサービスは成長が予想されるため、Web サイトと独立してスケーリングできるようにします。

このほか、データ ウェアハウスを導入してデータ分析機能を強化し、クラウドでトランザクション数が急増したときを中心に履歴データを随時分析できるようにすることを目指しています。OLTP データベースのデータを夜間に自社データ ウェアハウスに移行するソリューションを計画しており、理想的にはインフラストラクチャや開発の負担を最小限に抑えたいと考えています。

### 顧客のニーズ<a name="顧客のニーズ"></a>

1. インフラストラクチャのエンジニアリングを最小限に抑えて重要なビジネス価値の提供のために労力を活用できるようにするアーキテクチャを決定する。Contoso は PaaS ソリューションについて理解を深めたいと考えています。

2. PCI コンプライアンスの遵守を維持する。

3. システム全体で通信中と格納中のどちらの状態のデータもプライバシーを守り、保護する。

4. 商品推薦 API (Offers API) を Web サイトと独立してスケーリングできるようにする。

5. 目に見えない部分を変更して目的を達成する場合でも主要機能を維持する。

6. ユーザー名とパスワードの管理ソリューションを改良する。

7. リージョン単位でのデータベース フェールオーバー プランを導入し他のリージョンにフェールオーバーできるようにして、各種 Web アプリケーションやその他のホストされているサービスを同期されているデータベースに最小限のコストで引き継げるようにする。

8. データ ウェアハウスのトランザクション履歴を分析できるようにする。

### 顧客の反論<a name="顧客の反論"></a>


1. Azure トラスト センターを見ても、自社ソリューションを PCI に準拠させるにあたって Azure がどのように役立つのかわからなかった。

2. ソリューションをスケーリングして顧客の需要に対応しながら、同時にコール センターや倉庫のセキュリティを守ることができるか?

3. PCI コンプライアンスに準拠するには四半期ごとの監査が必要であり、侵入テストの実施が求められる場合もある。これは Azure で可能か?

4. Azure データ センターは監査可能か?

5. 過去に、Web サイトの大規模負荷テストの設計と実行に SOASTA CloudTest を利用した。Azure に移行しても引き続き CloudTest を使用できるか?

6. 従来のインフラストラクチャでは Web サイトのパフォーマンス監視機能が不十分だった。自社 Web アプリと連携する Azure のオプションにはどのようなものがあるか?

7. Azure のデータ ウェアハウスは一時停止できると聞いた。インスタンスを一時停止する前に Azure Storage の自社データをすべて保存する必要があるのか、またデータを損失するリスクがあるのか?

8. Azure SQL Database を自社データ ウェアハウスとして使用可能であることは理解した。Azure Synapse Analytics と比較する場合、どのような点について考慮すればよいか?

### 一般的なシナリオのインフォグラフィック<a name="一般的なシナリオのインフォグラフィック"></a>

![eコマース Web サイトの一般的なシナリオを示した図。エンド ユーザーから始まり、サービス層、インターネット層、データ層を経由して自社につながっている。また、Microsoft Azure と Azure Virtual Network が含まれている](media/image2.png 'eコマース Web サイトの一般的なシナリオを示した図')

## ステップ 2: 概念実証ソリューションの設計<a name="ステップ-2:-概念実証ソリューションの設計"></a>

**成果**

ソリューションを設計し、15 分の講義形式で提供先の顧客の担当者に行うソリューションのプレゼンテーションに向けて準備する。

時間: 60 分

**ビジネス ニーズ**

指示: 班の参加者全員で以下の質問に回答し、フリップ チャートに回答の一覧を記載します。

1. ソリューションを提案する相手は? 提案先の顧客の担当者は? 意思決定者は?

2. このソリューションで解決が必要な顧客のビジネス ニーズは?

**設計**

指示: 班の参加者全員でフリップ チャートに記載された以下の質問に回答します。

*アーキテクチャの概要*

1. 詳細については後のセクションで扱うため、ここでは詳細には触れずに、eコマース Web サイト、コール センター Web サイト、在庫の検索プロセスの大まかな要件に対応する初期構想を図示します。この図の内容は、進行に合わせて修正します。

*注文品の調達*

1. 在庫検索キューの管理方法を CSLA に推薦する方法、および CSLA が Azure Queues と Service Bus を選択する際にどのように補助するかについて決定します。分量、メッセージの有効期間、規模などを基に、CSLA の要件について考慮します。各項目の算出方法について説明します。

*通知*

1. CSLA の注文データベースで注文が処理されたときの顧客への通知を管理する方法、およびこれに利用できる Azure サービスについて検討します。CSLA に提案するソリューションへの実装や統合の詳細についても考慮します。

*Offers サービス*

1. Offers サービスの要件に対応するため、Contoso に Azure App Service API アプリの使用を提案することを検討します。

2. 提案する場合は、そのトポロジに適合する構成の詳細を検討します。特に、eコマース アプリケーションと Offers サービスのアプリケーション間の通信を許可するために必要な変更や構成を実装する方法について考慮します。

*地理的な回復性*

1. リージョン単位でデータ センターが停止した場合に備えて注文データベースに高可用性を実装する方法について検討します。特に、SQL Database と Azure Storage の構成を明確に決定します。

2. サービス停止発生時に Web アプリケーションや関連する Azure サービスの変更をセカンダリ リージョンにフェールオーバーするプロセスについて、どの方法を推薦するかを検討します。

3. フェールオーバーに要する時間やデータ損失が発生する時間の長さについて検討します。

*アクセス制御*

1. コール センター Web サイトへのアクセスの管理について、Contoso の要件を満たすソリューションを実装する方法をどのように推薦するかを検討します。実装方法と、提案したソリューションを Contoso が採用するように推薦する方法の両方を明確にします。

*PCI コンプライアンスの遵守*

1. PCI 遵守の観点からカード所有者のデータを保持するのは処理時のみ、eコマース Web サイト内のみに制限するため、以下の点を考慮して設計します。

    - Web アプリを Azure App Service Environment にデプロイすることを考慮します。

    - PCI の要件を遵守するにあたって Azure App Service Environment がどのように役立つか説明します。

    - App Service Environment の送受信トラフィックのセキュリティに最適化するため、PCI の遵守に必要なすべての送受信トラフィックの詳細を示し、Azure で運用できるようにします。これには、ソリューションの送受信トラフィック、eコマース Web サイトへの送信トラフィック、ソリューション内のアプリ間通信のトラフィックが含まれます。

    - 使用するネットワーク トポロジの詳細を説明できるようにします。

    - アプリケーション通信の全送受信トラフィックのセキュリティを守るために使用するメカニズムを詳細に示します。

    - 構成スクリプトを作成する場合は、スクリプトの例を示します。

2. Azure 仮想マシンの使用を推奨するかどうか検討します。また、推奨する理由、しない理由を説明します。

*データ ウェアハウス*

1. データ ウェアハウスの実装方法をどのように勧めるか検討します。

2. 夜間に OLTP データベースから自社データ ウェアハウスにデータを転送するようにスケジュールを設定する方法について検討します。

**準備**

指示: 班の参加者全員と以下を行います。

1. 提案したソリューションでは解決されない顧客のニーズを把握します。

2. ソリューションのメリットを把握します。

3. 顧客の反論に対応する方法を検討します。

15 分の講義形式で顧客に行うソリューションのプレゼンテーションに向けて準備します。

## ステップ 3: ソリューションのプレゼンテーション<a name="ステップ-3:-ソリューションのプレゼンテーション"></a>

**成果**

15 分の講義形式で提供先の顧客の担当者にソリューションのプレゼンテーションを行う。

時間: 30 分

**プレゼンテーション**

指示:

1. 他の班と組みます。

2. 一方の班はマイクロソフト チーム、もう一方の班は顧客を担当します。

3. マイクロソフト チームは、提案するソリューションのプレゼンテーションを顧客に向けて行います。

4. 顧客側は、反論リストの中からいずれかの反論を行います。

5. マイクロソフト チームは反論に対応します。

6. 顧客側はマイクロソフト チームにフィードバックを提供します。

7. 役割を入れ替えてステップ 2 ～ 6 を繰り返します。

## まとめ<a name="まとめ"></a>

時間: 15 分

指示: 各班が集まり、進行役や SME が事例に適したソリューションを発表します。

## 参考資料<a name="参考資料"></a>

| 説明                                                  | リンク        |
| :------------------------------------------------------------ | :--------------------------------- |
| コンプライアンスへの取り組み                                       |                              <https://www.microsoft.com/ja-jp/trust-center/compliance/compliance-overview>                              |
| Azure App Service                                          |                 <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/>                  |
| Azure Service Environment (ASE)                             |            <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-app-service-environment-intro/>            |
| ILB ASE を Azure Application Gateway と統合する            |             <https://docs.microsoft.com/ja-jp/azure/app-service/environment/integrate-with-application-gateway>             |
| ASE ネットワーク セキュリティ グループを構成する                      |            <https://docs.microsoft.com/ja-jp/azure/app-service/environment/network-info#network-security-groups>            |
| ASE を使用して地理的分散を実現する                               | <https://docs.microsoft.com/ja-jp/azure/app-service/environment/app-service-app-service-environment-geo-distributed-scale>  |
| Azure トラスト センター                                           |                                  <http://azure.microsoft.com/ja-jp/support/trust-center/>                                   |
| Azure PCI のコンプライアンス認定証 (英語)                         |   <http://download.microsoft.com/download/7/1/E/71E02A19-D1A4-448F-8CEA-D6A19398ABDA/Azure%20PCI%20AOC%20Feb%202015.pdf>    |
| PCI DSS v3.0 のドキュメント                                                |                               <https://www.pcisecuritystandards.org/documents/PCI_DSS_v3_2_1_JA-JP.pdf>                               |
| Azure Data Factory                                           | <https://azure.microsoft.com/ja-jp/documentation/articles/data-factory-data-movement-activities/#data-factory-copy-wizard/> |
| Azure SQL Database                                           |                <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-geo-replication-overview/>                 |
| Azure SQL Database を使用して高可用性サービスを設計する |     <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-designing-cloud-solutions-for-disaster-recovery>      |
| SQL Database 自動フェールオーバー グループ | <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-auto-failover-group?tabs=azure-powershell> |
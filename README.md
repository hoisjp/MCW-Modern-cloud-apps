<!--
# Modern cloud apps

The Contoso Sports League Association (CSLA) is one of the largest sports franchises and is struggling to keep up with demand from their growing user base. They currently host an e-commerce website and have a backend website that supports their call center, allowing employees to view order information.

CSLA would like to modernize their websites and move to the cloud, ultimately moving away from managing infrastructure. They are interested in whether Platform-as-a-Service (PaaS) will meet their needs so they can completely remove the infrastructure management overhead. However, they are concerned about securing their websites and data to meet the stringent PCI (Payment Card Industry) compliance requirements.

March 2020

## Target audience

Application developers

## Abstracts

### Workshop

In this workshop, you will work as a group to implement an end-to-end solution for e-commerce that is based on Azure App Services, Azure Active Directory, and Azure DevOps. You will ensure the solution is PCI compliant, and appropriate security measures are put into place for both on-premises and public access scenarios.

At the end of this workshop, you will be better able to deploy and configure Azure Web Apps and associated services. In addition, you will learn to configure Web Apps for authentication with Azure AD, instrument and load-test the application with App Insights, and automate back-end services using Azure Functions and Logic Apps.

### Whiteboard design session

In the whiteboard design session, you will work in groups to design a solution to modernize CSLA's e-commerce and back-end services while maintaining existing PCI compliance. To ensure compliance, you will ensure data privacy and protection across all aspects of the system, in transit and at rest. The goal is to use Azure PaaS services for the public-facing and back-end websites, while providing a way for the on-premises components to securely communicate with these services. You will also design fault-tolerance and a regional failover plan of the Azure components.

By the end of this whiteboard design session, you will have a better understanding of how to modernize a legacy web app by retargeting it for the cloud, taking advantage of the many services Azure provides to enhance functionality and secure your solution's components by following best practices for PCI compliance and security.

### Hands-on Lab

In this hands-on lab, you will be challenged to implement an end-to-end scenario using a supplied sample that is based on Azure App Services, Microsoft Azure Functions, Azure SQL Database, Azure Logic Apps, and related services. The scenario will include implementing compute, storage, workflows, and monitoring, using various components of Microsoft Azure.

Please note that as opposed to the Whiteboard Design Session, the lab is not focused on maintaining PCI compliance and using more advanced security features such as App Service Environment, Network Security Groups, and Application Gateway. The hands-on lab can be implemented on your own, but it is highly recommended to pair up with other members at the lab to model a real-world experience and to allow each member to share their expertise for the overall solution.

By the end of this hands-on lab, you will have learned how to use several key services within Azure to improve overall functionality of the original solution, and to increase the security and scalability of the new and improved design.

## Azure services and related products

- Azure App Service (Web App, API App)
- App Service Environment
- Azure Functions
- Application Gateway
- Azure Traffic Manager
- Azure Storage
- Azure Storage Queues
- Azure Data Factory
- Azure SQL Database
- Azure Active Directory
- Azure Logic Apps
- Azure DevOps
- Azure Application Insights
- Visual Studio 2019 Community Edition or later
- Twilio (third-party service to send SMS messages)

## Azure solutions

App Modernization

## Related references

- [MCW](https://github.com/Microsoft/MCW)

## Help & Support

We welcome feedback and comments from Microsoft SMEs & learning partners who deliver MCWs.  

***Having trouble?***
- First, verify you have followed all written lab instructions (including the Before the Hands-on lab document).
- Next, submit an issue with a detailed description of the problem.
- Do not submit pull requests. Our content authors will make all changes and submit pull requests for approval.   

If you are planning to present a workshop, *review and test the materials early*! We recommend at least two weeks prior.

### Please allow 5 - 10 business days for review and resolution of issues.
-->

# Modern cloud apps

Contoso Sports League Association (CSLA) は大手スポーツ フランチャイズで、成長を続けるユーザー ベースの需要への対応に苦戦しています。同社では現在 eコマース Web サイト、およびコール センターをサポートするバックエンド Web サイトをホストしていて、従業員が注文情報を表示できるようになっています。

CSLA はこの Web サイトを刷新してクラウドに移行し、最終的にはインフラストラクチャの管理を不要にしたいと考えています。サービスとしてのプラットフォーム (PaaS) でこのニーズに対応し、インフラストラクチャの管理オーバーヘッドを完全に排除できるのではないかと期待しています。ただし、Web サイトとデータがきわめて厳格な PCI (Payment Card Industry) のコンプライアンス要件を満たすことができるかどうか憂慮しています。

2020 年 3 月

## 対象となるお客様

アプリケーション開発者

## 要約

### ワークショップ

このワークショップでは、Azure App Services、Azure Active Directory、Azure DevOps を基盤とする eコマース用エンドツーエンド ソリューションを実装する作業をグループで行います。ソリューションは PCI に準拠し、オンプレミスと外部アクセスの両方で適切なセキュリティ対策が実装されている必要があります。

このワークショップを修了すると、Azure Web Apps や関連サービスのデプロイと構成を行うスキルが向上します。また、Azure AD での認証を Web Apps で構成する方法、App Insights でアプリケーションの計測や負荷テストを行う方法、Azure Functions と Logic Apps を使用してバックエンド サービスを自動化する方法を習得できます。

### ホワイトボード設計セッション

このホワイトボード設計セッションでは、CSLA の eコマース サービスとバックエンド サービスを刷新したソリューションをグループで設計します。ソリューションは、変更前と同様に PCI に準拠するものとします。コンプライアンスを遵守するため、システム全体で通信中と格納中のどちらの状態のデータもプライバシーを守り、保護する必要があります。目標は、外部に公開する Web サイトとバックエンド Web サイトに Azure PaaS サービスを使用すること、およびオンプレミス コンポーネントとこれらのサービスの間に安全な通信方法を実装することです。また、フォールト トレランスでリージョン内のフェールオーバーに対応した Azure コンポーネントを設計することが求められます。

このホワイトボード設計セッションを修了すると、レガシ Web アプリをクラウド向けに刷新する方法、および各種 Azure サービスを利用してソリューションのコンポーネントの機能や安全性を強化する方法を PCI 準拠やセキュリティのベスト プラクティスに従いながら習得できます。

### ハンズオン ラボ

このハンズオン ラボでは、Azure App Services、Azure Functions、Azure SQL Database、Azure Logic Apps、および関連サービスを基盤とする事例が提示され、それを使用してエンドツーエンドのシナリオを実装します。このシナリオでは、Microsoft Azure のさまざまなコンポーネントを使用してコンピューティング、ストレージ、ワークフロー、監視などを実装します。

このハンズオン ラボでは、ホワイトボード設計セッションとは異なり PCI への準拠にはこだわらず、App Service Environment、Network Security Groups、Application Gateway などの高度なセキュリティ機能を使用します。ハンズオン ラボは 1 人でも実装できますが、実際の状況を想定し、他のメンバーと協力してソリューション全体の専門知識を全員で共有することを強くおすすめします。

このハンズオン ラボを修了すると、主要な Azure サービスを複数使用して、元のソリューションの機能全般を改良すると共に、新規設計または改良されたソリューションの安全性とスケーラビリティを強化する方法を習得できます。

## Azure サービスと関連製品

- Azure App Service (Web アプリ、API アプリ)
- App Service Environment
- Azure Functions
- Application Gateway
- Azure Traffic Manager
- Azure Storage
- Azure Storage Queues
- Azure Data Factory
- Azure SQL Database
- Azure Active Directory
- Azure Logic Apps
- Azure DevOps
- Azure Application Insights
- Visual Studio 2019 Community Edition またはそれ以降
- Twilio (SMS メッセージ送信用サードパーティ サービス)

## Azure ソリューション

App Modernization

## 関連資料

- [MCW (英語)](https://github.com/Microsoft/MCW)

## ヘルプとサポート

マイクロソフトの SME や MCW の配信に携わる学習パートナーからのフィードバックやコメントをお待ちしています。  

***問題が発生したら***
- まず、ラボの指示書 (ハンズオン ラボ事前ガイドを含む) をすべて確認します。
- 次に、問題の詳細を記述した Issue を投稿します。
- プル リクエストは投稿しないでください。変更とプル リクエストによる承認要求は、すべてコンテンツ作成者が行います。   

ワークショップへの参加をご希望の方は、*お早めに資料を確認しテストを行ってください*。最低でも 2 週間の期間を見込むことをおすすめします。

### 問題の確認と解決に 5 ～ 10 営業日程度いただく場合があります。
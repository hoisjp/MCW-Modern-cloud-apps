<!--
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Modern cloud apps
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
March 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

# Modern cloud apps hands-on lab step-by-step

## Abstract and learning objectives

In this hands-on lab, you will be challenged to implement an end-to-end scenario using a supplied sample that is based on Azure App Services, Microsoft Azure Functions, Azure SQL Database, Azure Logic Apps, and related services. The scenario will include implementing compute, storage, workflows, and monitoring, using various components of Microsoft Azure.

Please note that as opposed to the whiteboard design session, the lab is not focused on maintaining PCI compliance and using more advanced security features such as App Service Environment, Network Security Groups, and Application Gateway. The hands-on lab can be implemented on your own, but it is highly recommended to pair up with other members working on the lab to model a real-world experience and to allow each member to share their expertise for the overall solution.

By the end of this hands-on lab, you will have learned how to use several key services within Azure to improve overall functionality of the original solution, and to increase the security and scalability of the new and improved design.

## Overview

The Cloud Workshop: Modern Cloud Apps lab is a hands-on exercise that will challenge you to implement an end-to-end scenario using a supplied sample that is based on Microsoft Azure App Services and related services. The scenario will include implementing compute, storage, security, and scale using various components of Microsoft Azure. The lab can be implemented on your own, but it is highly recommended to pair up with additional team members to more closely model a real-world experience, and to allow members to share their expertise for the overall solution.

## Solution architecture

![A diagram that depicts the various Azure PaaS services for the solution. Azure AD Org is used for authentication to the call center app. Azure AD B2C for authentication is used for authentication to the client app. SQL Database for the backend customer data. Azure App Services for the web and API apps. Order processing includes using Functions, Logic Apps, Queues and Storage. Azure App Insights is used for telemetry capture.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image2.png "Solution Architecture Diagram")

## Requirements

1. Microsoft Azure subscription
2. Local machine or a virtual machine configured with Visual Studio 2019 Community Edition
3. Twilio account and/or personal cell phone to setup a trial Twilio account

## Help references

| Description | Links |
|:---------|:-------------|
| SQL firewall | <https://azure.microsoft.com/en-us/documentation/articles/sql-database-configure-firewall-settings/> |
| Deploying a Web App | <https://azure.microsoft.com/en-us/documentation/articles/web-sites-deploy/> |
| Deploying an API app | <https://azure.microsoft.com/en-us/documentation/articles/app-service-dotnet-deploy-api-app/> |
| Accessing an API app from a JavaScript client | <https://azure.microsoft.com/en-us/documentation/articles/app-service-api-javascript-client/> |
| SQL Database Geo-Replication overview | <https://azure.microsoft.com/en-us/documentation/articles/sql-database-geo-replication-overview/> |
| What is Azure AD? | <https://azure.microsoft.com/en-us/documentation/articles/active-directory-whatis/> |
| Azure Web Apps authentication | <http://azure.microsoft.com/blog/2014/11/13/azure-websites-authentication-authorization/> |
| View your access and usage reports | <https://msdn.microsoft.com/en-us/library/azure/dn283934.aspx> |
| Custom branding an Azure AD Tenant | <https://msdn.microsoft.com/en-us/library/azure/Dn532270.aspx> |
| Service Principal Authentication | <https://docs.microsoft.com/en-us/azure/app-service-api/app-service-api-dotnet-service-principal-auth> |
| Consumer Site B2C | <https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-devquickstarts-web-dotnet> |
| Getting Started with Active Directory B2C | <https://azure.microsoft.com/en-us/trial/get-started-active-directory-b2c/> |
| How to Delete an Azure Active Directory | <https://blog.nicholasrogoff.com/2017/01/20/how-to-delete-an-azure-active-directory-add-tenant/> |
| Run performance tests on your app | <http://blogs.msdn.com/b/visualstudioalm/archive/2015/09/15/announcing-public-preview-for-performance-load-testing-of-azure-webapp.aspx> |
| Application Insights Custom Events | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-api-custom-events-metrics/> |
| Enabling Application Insights | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-start-monitoring-app-health-usage/> |
| Detect failures | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-asp-net-exceptions/> |
| Monitor performance problems | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-web-monitor-performance/> |
| Creating a Logic App | <https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-create-a-logic-app/> |
| Logic app connectors | <https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-connectors-list/> |
| Logic Apps Docs | <https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-what-are-logic-apps> |
| Azure Functions -- create first function | <https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-azure-function> |
| Azure Functions docs | <https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-azure-functions> |

-->
![Microsoft Cloud Workshop](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshop")

<div class="MCWHeader1">
最新のクラウド アプリ
</div>

<div class="MCWHeader2">
ステップバイステップ式ハンズオン ラボ
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
- [最新のクラウド アプリ ステップバイステップ式ハンズオン ラボ](#最新のクラウド-アプリ-ステップバイステップ式ハンズオン-ラボ)
  - [要約と学習目標](#要約と学習目標)
  - [概要](#概要)
  - [ソリューションのアーキテクチャ](#ソリューションのアーキテクチャ)
  - [前提条件](#前提条件)
  - [関連ヘルプ記事](#関連ヘルプ記事)
  - [演習 1: 概念実証版のデプロイ](#演習-1:-概念実証版のデプロイ)
    - [タスク 1: eコマースの Web サイト、SQL Database、ストレージをデプロイする](#タスク-1:-eコマースの-Web-サイト、SQL-Database、ストレージをデプロイする)
      - [サブタスク 1: SQL Database のファイアウォールを構成し接続文字列を取得する](#サブタスク-1:-SQL-Database-のファイアウォールを構成し接続文字列を取得する)
      - [サブタスク 2: ストレージ アカウントのアクセス キーを取得する](#サブタスク-2:-ストレージ-アカウントのアクセス-キーを取得する)
      - [サブタスク 3: Service Bus キューの接続文字列を取得する](#サブタスク-3:-Service-Bus-キューの接続文字列を取得する)
      - [サブタスク 4: スターター プロジェクトの構成を更新する](#サブタスク-4:--スターター-プロジェクトの構成を更新する)
      - [サブタスク 5: Visual Studio から eコマース Web アプリをデプロイする](#サブタスク-5:-Visual-Studio-から-eコマース-Web-アプリをデプロイする)
    - [タスク 2: SQL Database の geo レプリケーションをセットアップする](#タスク-2:-SQL-Database-の-geo-レプリケーションをセットアップする)
      - [サブタスク 1: セカンダリ データベースを追加する](#サブタスク-1:-セカンダリ-データベースを追加する)
      - [サブタスク 2: SQL フェールオーバー グループをセットアップする](#サブタスク-2:-SQL-フェールオーバー-グループをセットアップする)
      - [サブタスク 3: SQL Database フェールオーバー グループのフェールオーバーを実行する](#サブタスク-3:-SQL-Database-フェールオーバー-グループのフェールオーバーを実行する)
      - [サブタスク 4: フェールオーバー後に eコマース Web アプリをテストする](#サブタスク-4:-フェールオーバー後に-eコマース-Web-アプリをテストする)
    - [タスク 3: コール センター管理 Web サイトをデプロイする](#タスク-3:-コール-センター管理-Web-サイトをデプロイする)
      - [サブタスク 1: コール センター管理 Web アプリをプロビジョニングする](#サブタスク-1:-コール-センター管理-Web-アプリをプロビジョニングする)
      - [サブタスク 2: スターター プロジェクトの構成を更新する](#サブタスク-2:-スターター-プロジェクトの構成を更新する)
      - [サブタスク 3: Visual Studio からコール センター管理 Web アプリをデプロイする](#サブタスク-3:-Visual-Studio-からコール-センター管理-Web-アプリをデプロイする)
    - [タスク 4: 支払いゲートウェイをデプロイする](#タスク-4:-支払いゲートウェイをデプロイする)
      - [サブタスク 1: 支払いゲートウェイ API アプリをプロビジョニングする](#サブタスク-1:-支払いゲートウェイ-API-アプリをプロビジョニングする)
      - [サブタスク 2: Visual Studio から Contoso.Apps.PaymentGateway プロジェクトをデプロイする](#サブタスク-2:-Visual-Studio-から-Contoso.Apps.PaymentGateway-プロジェクトをデプロイする)
    - [タスク 5: Offers Web API をデプロイする](#タスク-5:-Offers-Web-API-をデプロイする)
      - [サブタスク 1: Offers Web API アプリをプロビジョニングする](#サブタスク-1:-Offers-Web-API-アプリをプロビジョニングする)
      - [サブタスク 2: クロス オリジン リソース共有 (CORS) を構成する](#サブタスク-2:-クロス-オリジン-リソース共有-(CORS)-を構成する)
      - [サブタスク 3: スターター プロジェクトの構成を更新する](#サブタスク-3:-スターター-プロジェクトの構成を更新する)
      - [サブタスク 4: Visual Studio から Contoso.Apps.SportsLeague.Offers プロジェクトをデプロイする](#サブタスク-4:-Visual-Studio-から-Contoso.Apps.SportsLeague.Offers-プロジェクトをデプロイする)
    - [タスク 6: eコマース Web サイトを更新してデプロイする](#タスク-6:-eコマース-Web-サイトを更新してデプロイする)
      - [サブタスク 1: Contoso.Apps.SportsLeague.Web プロジェクトをホストする Web アプリケーションの設定を更新する](#サブタスク-1:-Contoso.Apps.SportsLeague.Web-プロジェクトをホストする-Web-アプリケーションの設定を更新する)
      - [サブタスク 2: アプリケーション設定が適切であることを検証する](#サブタスク-2:-アプリケーション設定が適切であることを検証する)
  - [演習 2: ID とセキュリティ](#演習-2:-ID-とセキュリティ)
    - [タスク 1: Azure AD Premium 試用版を有効化する](#タスク-1:-Azure-AD-Premium-試用版を有効化する)
    - [タスク 2: Contoso ユーザーを新規作成する](#タスク-2:-Contoso-ユーザーを新規作成する)
    - [タスク 3: コール センター管理 Web アプリケーションのアクセス制御を構成する](#タスク-3:-コール-センター管理-Web-アプリケーションのアクセス制御を構成する)
      - [サブタスク 1: Azure AD 認証を有効化する](#サブタスク-1:-Azure-AD-認証を有効化する)
      - [サブタスク 2: コール センター管理 Web サイトへのログオンにアクセス制御が適用されていることを検証する](#サブタスク-2:-コール-センター管理-Web-サイトへのログオンにアクセス制御が適用されていることを検証する)
    - [タスク 4: Azure Active Directory のログオン ページにカスタム ブランディングを適用する](#タスク-4:-Azure-Active-Directory-のログオン-ページにカスタム-ブランディングを適用する)
    - [タスク 5: Azure Active Directory のログオン ページにブランディングが正常に適用されていることを検証する](#タスク-5:-Azure-Active-Directory-のログオン-ページにブランディングが正常に適用されていることを検証する)
  - [演習 3: 顧客サイト用 Azure B2C を有効化する](#演習-3:-顧客サイト用-Azure-B2C-を有効化する)
    - [タスク 1: ディレクトリを新規作成する](#タスク-1:-ディレクトリを新規作成する)
    - [タスク 2: アプリケーションを新規作成する](#タスク-2:-アプリケーションを新規作成する)
    - [タスク 3: サインアップとサインインのポリシーを作成する](#タスク-3:-サインアップとサインインのポリシーを作成する)
    - [タスク 4: プロファイル編集ポリシーを作成する](#タスク-4:-プロファイル編集ポリシーを作成する)
    - [タスク 5: パスワード リセット ポリシーを作成する](#タスク-5:-パスワード-リセット-ポリシーを作成する)
    - [タスク 6: Contoso.App.SportsLeague.Web を変更する](#タスク-6:-Contoso.App.SportsLeague.Web-を変更する)
    - [タスク 7: 認証要求を Azure AD に送信する](#タスク-7:-認証要求を-Azure-AD-に送信する)
    - [タスク 8: ユーザー情報を表示する](#タスク-8:-ユーザー情報を表示する)
    - [タスク 9: サンプル アプリを実行する](#タスク-9:-サンプル-アプリを実行する)
  - [演習 4: Application Insights でテレメトリを有効化する](#演習-4:-Application-Insights-でテレメトリを有効化する)
    - [タスク 1: アプリケーションでテレメトリを構成する](#タスク-1:-アプリケーションでテレメトリを構成する)
      - [サブタスク 1: eコマース Web サイト プロジェクトに Application Insights Telemetry を追加する](#サブタスク-1:-eコマース-Web-サイト-プロジェクトに-Application-Insights-Telemetry-を追加する)
      - [サブタスク 2: クライアント側のテレメトリを有効化する](#サブタスク-2:-クライアント側のテレメトリを有効化する)
      - [サブタスク 3: Visual Studio から eコマース Web アプリをデプロイする](#サブタスク-3:-Visual-Studio-から-eコマース-Web-アプリをデプロイする)
    - [タスク 2: Web のパフォーマンス テストと負荷テストを作成する](#タスク-2:-Web-のパフォーマンス-テストと負荷テストを作成する)
      - [サブタスク 1: 負荷テストを作成する](#サブタスク-1:-負荷テストを作成する)
      - [サブタスク 2: Application Insights のログを表示する](#サブタスク-2:-Application-Insights-のログを表示する)
  - [演習 5: Azure Functions と Logic Apps でバックエンド処理を自動化する](#演習-5:-Azure-Functions-と-Logic-Apps-でバックエンド処理を自動化する)
    - [タスク 1: PDF 形式の受領書を生成する Azure 関数を作成する](#タスク-1:-PDF-形式の受領書を生成する-Azure-関数を作成する)
    - [タスク 2: 注文を処理する Azure Logic Apps を作成する](#タスク-2:-注文を処理する-Azure-Logic-Apps-を作成する)
    - [タスク 3: Twilio を使用して SMS で注文通知を送信する](#タスク-3:-Twilio-を使用して-SMS-で注文通知を送信する)
      - [サブタスク 1: Twilio の試用アカウントを構成する](#サブタスク-1:-Twilio-の試用アカウントを構成する)
      - [サブタスク 2: 新しいロジック アプリを作成する](#サブタスク-2:-新しいロジック-アプリを作成する)
  - [ハンズオン ラボ終了後の作業](#ハンズオン-ラボ終了後の作業)
    - [タスク 1: リソースを削除する](#タスク-1:-リソースを削除する)

<!-- /TOC -->

# 最新のクラウド アプリ ステップバイステップ式ハンズオン ラボ<a name="最新のクラウド-アプリ-ステップバイステップ式ハンズオン-ラボ"></a>

## 要約と学習目標<a name="要約と学習目標"></a>

このハンズオン ラボでは、用意されたサンプルに従って、Azure App Service、Azure Functions、Azure SQL Database、Azure Logic Apps、および関連サービスを基盤とするエンドツーエンドのシナリオを実装します。具体的には、Microsoft Azure のさまざまなコンポーネントを使用してコンピューティング、ストレージ、ワークフロー、監視などを実装します。

このハンズオン ラボでは、ホワイトボード設計セッションとは異なり PCI への準拠にはこだわりません。また、App Service Environment、Network Security Groups、Application Gateway などの高度なセキュリティ機能を使用します。ハンズオン ラボは 1 人でも実装できますが、実際の状況を想定し、他のメンバーと協力してソリューション全体の専門知識を全員で共有することを強くおすすめします。

このハンズオン ラボを修了すると、主要な Azure サービスを複数使用して、元のソリューションの機能全般を改良すると共に、新規設計または改良されたソリューションの安全性とスケーラビリティを強化する方法を習得できます。

## 概要<a name="概要"></a>

Cloud Workshop: 最新のクラウド アプリ ラボは、用意されたサンプルに従って Microsoft Azure App Service および関連サービスを基盤とするエンドツーエンドのシナリオを実装する、ハンズオン形式の演習です。このシナリオでは、Microsoft Azure のさまざまなコンポーネントを使用してコンピューティング、ストレージ、セキュリティ、スケーリングなどを実装します。ラボは 1 人でも実装できますが、実際の状況を想定し、他のメンバーと緊密に協力してソリューション全体の専門知識を全員で共有することを強くおすすめします。

## ソリューションのアーキテクチャ<a name="ソリューションのアーキテクチャ"></a>

![ソリューションで使用する各種 Azure PaaS サービスの図。コール センター アプリの認証には Azure AD Org を使用。クライアント アプリの認証には Azure AD B2C を使用。バックエンドの顧客データには SQL Database を使用。Web アプリと API アプリには Azure App Service を使用。注文処理には Functions、Logic Apps、キュー、Storage などを使用。テレメトリの取得には Azure App Insights を使用](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image2.png "ソリューション アーキテクチャ図")

## 前提条件<a name="前提条件"></a>

1. Microsoft Azure サブスクリプション
2. Visual Studio 2019 Community Edition が構成されたローカル マシンまたは仮想マシン
3. Twilio アカウント、または Twilio の試用アカウントのセットアップに使用する個人用携帯電話のいずれかまたはその両方。

## 関連ヘルプ記事<a name="関連ヘルプ記事"></a>

| 説明 | リンク |
|:---------|:-------------|
| SQL のファイアウォール | <https://azure.microsoft.com/ja-jp/documentation/articles/sql-database-configure-firewall-settings/> |
| Web アプリのデプロイ | <https://azure.microsoft.com/ja-jp/documentation/articles/web-sites-deploy/> |
| API アプリのデプロイ | <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-dotnet-deploy-api-app/> |
| JavaScript クライアントから API アプリへのアクセス | <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-api-javascript-client/> |
| SQL Database の geo レプリケーションの概要 | <https://azure.microsoft.com/ja-jp/documentation/articles/sql-database-geo-replication-overview/> |
| Azure AD の概要| <https://azure.microsoft.com/ja-jp/documentation/articles/active-directory-whatis/> |
| Azure Web Apps の認証 | <http://azure.microsoft.com/blog/2014/11/13/azure-websites-authentication-authorization/> (英語) |
| アクセス レポートと使用状況レポートの表示 | <https://msdn.microsoft.com/en-us/library/azure/dn283934.aspx> (英語) |
| Azure AD テナントのカスタム ブランディング | <https://msdn.microsoft.com/en-us/library/azure/Dn532270.aspx> (英語) |
| サービス プリンシパルの認証 | <https://docs.microsoft.com/ja-jp/azure/app-service-api/app-service-api-dotnet-service-principal-auth> |
| 一般ユーザー向けサイトの B2C | <https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/active-directory-b2c-devquickstarts-web-dotnet> |
| Active Directory B2C の使用開始 | <https://azure.microsoft.com/ja-jp/trial/get-started-active-directory-b2c/> |
| Azure Active Directory の削除方法 | <https://blog.nicholasrogoff.com/2017/01/20/how-to-delete-an-azure-active-directory-add-tenant/> (英語) |
| アプリのパフォーマンス テストの実行 | <https://devblogs.microsoft.com/devops/announcing-public-preview-for-performanceload-testing-of-azure-webapp/> (英語) |
| Application Insights のカスタム イベント | <https://azure.microsoft.com/ja-jp/documentation/articles/app-insights-api-custom-events-metrics/> |
| Application Insights の有効化 | <https://azure.microsoft.com/ja-jp/documentation/articles/app-insights-start-monitoring-app-health-usage/> |
| 障害の検出 | <https://azure.microsoft.com/ja-jp/documentation/articles/app-insights-asp-net-exceptions/> |
| パフォーマンスの問題の監視 | <https://azure.microsoft.com/ja-jp/documentation/articles/app-insights-web-monitor-performance/> |
| ロジック アプリの作成 | <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-logic-create-a-logic-app/> |
| Logic Apps のコネクタ | <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-logic-connectors-list/> |
| Logic Apps のドキュメント | <https://docs.microsoft.com/ja-jp/azure/logic-apps/logic-apps-what-are-logic-apps> |
| Azure Functions - 初めての関数作成 | <https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-create-first-azure-function> |
| Azure Functions のドキュメント | <https://docs.microsoft.com/ja-jp/azure/logic-apps/logic-apps-azure-functions> |
<!--
## Exercise 1: Proof of concept deployment

Duration: 60 minutes

Contoso has asked you to create a proof of concept deployment in Microsoft Azure by deploying the web, database, and API applications for the solution as well as validating that the core functionality of the solution works. Ensure all resources use the same resource group previously created for the App Service Environment.

### Task 1: Deploy the e-commerce website, SQL Database, and storage

In this exercise, you will provision a website via the Azure **Web App + SQL** template using the Microsoft Azure Portal. You will then edit the necessary configuration files in the starter project and deploy the e-commerce website.

#### Subtask 1: Configure SQL Database Firewall and Retrieve Connection String

1. Navigate to the Azure Management portal, [http://portal.azure.com](http://portal.azure.com/), using a new tab or instance and login with your lab-provided Azure credentials.

2. Navigate to the **contososports** resource group.

3. Select the **ContosoSportsDB** SQL Database.

    ![The contososports Resource Group blade with the "ContosoSportsDB" highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image22.png "Azure Portal")

4. On the **SQL Database** blade, select the **Show database connection strings** link.

    ![On the SQL Database blade, in the left pane, Overview is selected. In the right pane, under Essentials, the Connection strings (Show database connection strings) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image23.png "SQL Database blade")

5. On the **Database connection strings** blade, select and copy the **ADO.NET** connection string. Then, save it in **Notepad** for use later, being sure to replace the placeholders with your username and password with **demouser** and **demo@pass123**, respectively.

    ![In the Database connection strings blade, the ADO.NET connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image24.png "Database connection strings blade")

6. Go back to the **contososports** resource group blade, and select the **contososports** SQL Server.

    ![The contososports resource group with the contososports sql server highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/2019-11-15-17-47-46.png "Azure Portal")

7. On the **Overview** screen of the **SQL Server** blade, select **Set server firewall** link at the top.

    ![In the SQL Server Blade, Overview section, the Set server firewall tile is in a box.](media/2019-03-31-14-37-31.png "SQL Server Blade, Essentials section")

8. On the **Firewall Settings** blade, specify a new rule named **ALL**, with START IP **0.0.0.0**, and END IP **255.255.255.255**.

    ![Screenshot of the Rule name, Start IP. and End IP fields on the Firewall Settings blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "Firewall Settings blade")

    >**Note**: This is only done to make the lab easier to do. In production, you do **NOT** want to open your SQL Database to all IP Addresses this way. Instead, you will want to specify just the IP Addresses you wish to allow through the Firewall.

9. Select **Save**.

    ![Screenshot of the Firewall settings Save button.](media/2019-04-10-16-00-29.png "Firewall settings Save button")

10. Update progress can be found by selecting the **Notifications** link located at the top of the page.

    ![Screenshot of the Success dialog box, which says that the server firewall rules have been successfully updated.](media/2019-04-19-13-39-41.png "Success dialog box")

11. Close all configuration blades.

#### Subtask 2: Retrieve Storage Account Access Keys

1. Go back to the **contososports** blade resource group, and select the **contoso** Storage account.

2. On the **Storage account** blade, scroll down, and, under the **SETTINGS** menu area, select the **Access keys** option.

    ![In the Storage account blade, under Settings, Access keys is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image35.png "Storage account blade")

3. On the **Access keys** blade, select the copy button by the **Connection String** field in the **key1** section. Paste the value into **Notepad** for later usage. 

    ![In the Access keys blade default keys section, the copy button for the key1 connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image36.png "Access keys blade, default keys section")

#### Subtask 3: Retrieve Service Bus Queue Connection String

1. Go back to the **contososports** blade resource group, and select the **contoso** Service Bus Namespace.

    ![Service Bus Namespace resource is highlighted](media/2020-03-18-10-38-09.png "Service Bus Namespace")

2. Select the **Queues** link under Entities.

    ![Queues link under Entities](media/2020-03-18-10-38-57.png "Queues link")

3. On the **Queues** pane, select the **receiptgenerator** Service Bus Queue.

    ![receiptgenerator queue is highlighted](media/2020-03-18-10-40-40.png "receiptgenerator queue is highlighted")

4. On the **receiptgenerator** Service Bus Queue blade, select the **Shared access policies** link under Settings.

    ![Shared access policies link is shown](media/2020-03-18-10-42-03.png "Shared access policies link is shown")

5. Select the **Publisher** shared access policy.

    ![Publisher policy is highlighted](media/2020-03-18-10-43-12.png "Publisher policy is highlighted")

    >**Note**: The _Publisher_ and _Listener_ shared access policies for the Azure Service Bus Queue were deployed as part of the ARM Template that was used to setup the lab environment. As you can see, the **Publisher** policy that we're copying the connection string for, only has permissions to _Send_ messages to the queue.
    >
    > By default, no policies are created. Additionally, it is best practice to use least privilege security to create separate shared access policies for publishers sending messages and listeners receiving messages from the queue. 

6. On the **SAS Policy** pane, copy the **Primary Connection String**. Paste the value into **Notepad** for later usage. 

    ![Primary Connection String is highlighted](media/2020-03-18-10-54-39.png "Primary Connection String is highlighted")

#### Subtask 4: Update the configuration in the starter project

1. Go back to the **contososports** resource group blade.

2. Select the **contosoapp** web app (**App Service** type).

    ![Resources listed for ContosoSports. Web app selected.](media/2019-04-19-13-46-40.png "Resources listed for ContosoSports")

3. Copy the web app URL to Notepad.

    - Select the **Overview** link.
    - Copy the URL to Notepad for later use. Use the **Copy to clipboard** link.

    ![In the Web App Overview settings, the URL has a box around the link.](media/2019-03-22-16-33-05.png "Contoso Web App Overview")

4. On the **App Service** blade, scroll down in the left pane. Under the **Settings** menu, select **Configuration**.

    ![In the App Service blade, under Settings, select Configuration link.](media/2019-04-19-16-38-54.png "Configuration link")

5. Add a new **Application setting** with the following values:

   - Key: `AzureQueueConnectionString`

   - Value: Enter the Connection String for the **Azure Service Bus Queue** just created.

    ![In the App settings section for the App Service blade, the new entry for AzureQueueConnectionString is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image40.png "App settings section")

6. Locate **Connection Strings** section below **Application Settings**.

    ![The Connection Strings section for the App Service blade displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image41.png "Connection Strings section")

7. Add a new **Connection String** with the following values:

   - Name: `ContosoSportsLeague`

   - Value: **Enter the Connection String for the SQL Database just created**.

   - Type: `SQLAzure`

    >**Important**: Ensure you replace the string placeholder values **{your\_username}** **{your\_password\_here}** with the username and password you setup during previously.

    ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder value")

8. Select **Save**.

#### Subtask 5: Deploy the e-commerce Web App from Visual Studio

1. Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** of Visual Studio.

    ![In Solution Explorer, under Solution \'Contoso.Apps.SportsLeague\' (7 projects), Web is expanded, and under Web, Contoso.Apps.SportsLeague.Web is selected.](media/2019-04-19-14-03-04.png "Solution Explorer")

2. Right-click the **Contoso.Apps.SportsLeague.Web** project, and select **Publish**.

    >**Note**: Don't publish if the configuration does not show your settings. Choose **New Profile** to publish to your Azure subscription.
    > 
    > ![Visual Studio Publish configuration left over from developer. A don't publish message is displayed. There is a box around New Profile link.](media/2019-03-22-12-42-48.png "Select New Profile")

3. Choose **Azure App Service** as the publish target, and choose **Select Existing** and then **Create Profile** at the bottom of the wizard.

    ![On the Publish tab, the Microsoft Azure App Service tile is selected, as is the radio button for Select Existing.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image47.png "Publish tab")

4. If prompted, log on with your Azure Subscription credentials.

    ![App Service Select Existing App Service dialog is displayed. The Sign In link is highlighted](media/2019-04-19-14-07-19.png "Azure Sign In")

    >**Note**: If you Sign In and nothing happens, shut down Visual Studio reopen to the solution. Repeat the publishing steps.

5. Select the **Contoso Sports Web App** (with the name you created previously).

    ![Under Subscriptions, under contososports, contososportsweb0 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image49.png "Subscriptions")

6. Select **OK**.

7. Select **Publish** to publish the Web application.

    >**Note**: If prompted with a warning about App Service supporting .NET Core 3.0.0, select **OK** to dismiss the warning.
    >
    > ![App Service .NET Core 3.0.0 support warning.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/2019-11-15-18-12-21.png "App Service .NET Core 3.0.0 support warning")

8. In the Visual Studio **Output** view, you will see a status that indicates the Web App was published successfully.

    ![Screenshot of the Visual Studio Output view, with the Publish Succeeded message circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image50.png "Visual Studio Output view")

    >**Note**: Your URL will differ from the one shown in the Output screenshot because it must be globally unique.

9. A new browser should automatically open the new web applications. Validate the website by choosing the **Store** link on the menu. You should see product items. If products are returned, then the connection to the database is successful.

    ![Screenshot of the Store link.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image51.png "Store link")

    >**Troubleshooting**: If the web site fails to show products, go back and double check all your connection string entries and passwords web application settings.

-->
## 演習 1: 概念実証版のデプロイ<a name="演習-1:-概念実証版のデプロイ"></a>

時間: 60 分

Microsoft Azure 上に概念実証版デプロイメントを作成してほしいという依頼を Contoso から受けたため、ソリューションで使用する Web アプリ、データベース アプリ、API アプリのデプロイや、ソリューションの主要機能の動作検証などを行います。リソースは、必ず前の手順で作成した App Service Environment 用のリソース グループのものを使用します。

### タスク 1: eコマースの Web サイト、SQL Database、ストレージをデプロイする<a name="タスク-1:-eコマースの-Web-サイト、SQL-Database、ストレージをデプロイする"></a>

この演習では、Azure **Web Apps と SQL** のテンプレートを使用して Azure Portal から Web サイトをプロビジョニングします。その後、スターター プロジェクト内の構成ファイル群を必要に応じて編集し、eコマース Web サイトをデプロイします。

#### サブタスク 1: SQL Database のファイアウォールを構成し接続文字列を取得する<a name="サブタスク-1:-SQL-Database-のファイアウォールを構成し接続文字列を取得する"></a>

1. 新規のタブまたはインスタンスで Azure 管理ポータル (<http://portal.azure.com>) にアクセスし、ラボで指定された Azure 資格情報でログインします。

2. **contososports** リソース グループに移動します。

3. **ContosoSportsDB** という SQL Database を選択します。

    ![contososports リソース グループ ブレードで「ContosoSportsDB」が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image22.png "Azure Portal")

4. [**SQL Database**] ブレードで [**データベース接続文字列の表示**] リンクを選択します。

    ![[SQL Database] ブレード左側のウィンドウで [概要] が選択されている。右側のウィンドウにある [概要] の [接続文字列] (データベース接続文字列の表示) のリンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image23.png "[SQL Database] ブレード")

5. [**データベース接続文字列**] ブレードで **ADO.NET** の接続文字列を選択してコピーし、後で使用するため**メモ帳**に保存します。プレースホルダー内のユーザー名を **demouser**、パスワードを **demo@pass123** に変更します。

    ![[データベース接続文字列] ブレードの ADO.NET の接続文字列が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image24.png "[データベース接続文字列] ブレード")

6. **contososports** リソース グループ ブレードに戻り、**contososports** という SQL Server を選択します。

    ![contososports リソース グループで contososports SQL Server が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/2019-11-15-17-47-46.png "Azure Portal")

7. [**SQL Server**] ブレードの [**概要**] セクション上部にある [**サーバー ファイアウォールの設定**] リンクをクリックします。

    ![[SQL Server] ブレードの [概要] セクションの [サーバー ファイアウォールの設定] タイルが囲まれている](media/2019-03-31-14-37-31.png "[SQL Server] ブレードの [概要] セクション")

8. [**ファイアウォール設定**] ブレードで、名称が **ALL**、開始 IP が **0.0.0.0**、終了 IP が **255.255.255.255** のルールを新規作成します。

    ![[ファイアウォール設定] ブレードのルール名、開始 IP、終了 IP の各フィールドを示すスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "[ファイアウォール設定] ブレード")

    >**注**: このラボでは、わかりやすいようにこのような設定にします。運用環境では、この例のようにすべての IP アドレスから SQL Database へのアクセスを許可する設定は**適切ではありません**。ファイアウォールの通過を許可する IP アドレスのみを指定します。

9. [**保存**] をクリックします。

    ![ファイアウォール設定の [保存] ボタンのスクリーンショット](media/2019-04-10-16-00-29.png "ファイアウォール設定の [保存] ボタン")

10. ページ上部の [**通知**] リンクをクリックすると、更新の進捗状況を確認できます。

    ![サーバーのファイアウォール規則が正常に更新されたことを示すダイアログ ボックス](media/2019-04-19-13-39-41.png "更新成功を示すダイアログ ボックス")

11. 構成ブレードをすべて閉じます。

#### サブタスク 2: ストレージ アカウントのアクセス キーを取得する<a name="サブタスク-2:-ストレージ-アカウントのアクセス-キーを取得する"></a>

1. **contososports** リソース グループ ブレードに戻り、**contoso** ストレージ アカウントを選択します。

2. [**ストレージ アカウント**] ブレードを下方向にスクロールして [**設定**] メニューから [**アクセス キー**] オプションを選択します。

    ![[ストレージ アカウント] ブレードの [設定] の [アクセス キー] が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image35.png "[ストレージ アカウント] ブレード")

3. [**アクセス キー**] ブレードで [**キー 1**] セクションの**接続文字列**の横にあるコピー ボタンをクリックします。後で使用するため、この値を**メモ帳**に貼り付けます。 

    ![[アクセス キー] ブレードの既定のキー セクションでキー 1 の接続文字列のコピー ボタンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image36.png "[アクセス キー] ブレードの既定のキー セクション")

#### サブタスク 3: Service Bus キューの接続文字列を取得する<a name="サブタスク-3:-Service-Bus-キューの接続文字列を取得する"></a>

1. **contososports** リソース グループ ブレードに戻り、**contoso** の Service Bus 名前空間を選択します。

    ![Service Bus 名前空間のリソースが強調表示されている](media/2020-03-18-10-38-09.png "Service Bus 名前空間")

2. [エンティティ] で [**キュー**] リンクをクリックします。

    ![[エンティティ] の [キュー] リンク](media/2020-03-18-10-38-57.png "[キュー] リンク")

3. [**キュー**] ウィンドウで **receiptgenerator** という Service Bus キューを選択します。

    ![receiptgenerator キューが強調表示されている](media/2020-03-18-10-40-40.png "receiptgenerator キューが強調表示されている")

4. **receiptgenerator** の Service Bus キュー ブレードの [設定] で [**共有アクセス ポリシー**] リンクをクリックします。

    ![[共有アクセス ポリシー] リンクが表示されている](media/2020-03-18-10-42-03.png "[共有アクセス ポリシー] リンクが表示されている")

5. **Publisher** 共有アクセス ポリシーを選択します。

    ![Publisher ポリシーが強調表示されている](media/2020-03-18-10-43-12.png "Publisher ポリシーが強調表示されている")

    >**注**: Azure Service Bus キューの _Publisher_ および _Listener_ の共有アクセス ポリシーは、ラボ環境のセットアップに使用した ARM テンプレートの一部としてデプロイされています。図に示したように、接続文字列をコピーしようとしている **Publisher** ポリシーには、メッセージのキューへの _Send_ のみが許可されています。
    >
    > 既定では、作成済みのポリシーはありません。なお、キューにメッセージを送信するパブリッシャーとキューからメッセージを受信するリスナーには個別に共有アクセス ポリシーを作成し、最小限のセキュリティ権限を設定することをおすすめします。 

6. [**SAS ポリシー**] ウィンドウで [**プライマリ接続文字列**] の値をコピーします。後で使用するため、この値を**メモ帳**に貼り付けます。 

    ![[プライマリ接続文字列] が強調表示されている](media/2020-03-18-10-54-39.png "[プライマリ接続文字列] が強調表示されている")

#### サブタスク 4: スターター プロジェクトの構成を更新する<a name="サブタスク-4:--スターター-プロジェクトの構成を更新する"></a>

1. **contososports** リソース グループ ブレードに戻ります。

2. **contosoapp** Web アプリ (種類は **App Service**) を選択します。

    ![ContosoSports のリソースのリスト。Web アプリが選択されている](media/2019-04-19-13-46-40.png "ContosoSports のリソースのリスト")

3. Web アプリの URL をメモ帳にコピーします。

    - [**概要**] リンクを選択します。
    - 後で使用するため、URL をメモ帳にコピーします。[**クリップボードにコピー**] リンクを使用します。

    ![Web アプリの [概要] 設定のリンクの URL が囲まれている](media/2019-03-22-16-33-05.png "Contoso Web アプリの概要")

4. [**App Service**] ブレードの左側のウィンドウを下方向にスクロールします。[**設定**] メニューで [**構成**] をクリックします。

    ![[App Service] ブレードの [設定] で [構成] リンクをクリック](media/2019-04-19-16-38-54.png "[構成] リンク")

5. **アプリケーション設定**を新規追加し、以下の値を指定します。

   - キー: `AzureQueueConnectionString`

   - 値: 前の手順で作成した **Azure Service Bus キュー**の接続文字列を入力します。

    ![[App Service] ブレードの [アプリケーション設定] セクションで新規エントリの AzureQueueConnectionString が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image40.png "[アプリケーション設定] セクション")

6. [**アプリケーション設定**] の [**接続文字列**] セクションに移動します。

    ![[App Service] ブレードの [接続文字列] セクションの表示](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image41.png "[接続文字列] セクション")

7. 以下の値を持つ**接続文字列**を新規追加します。

   - 名前: `ContosoSportsLeague`

   - 値: 前の手順で作成した **SQL Database** の接続文字列を入力します。

   - 種類: `SQLAzure`

    >**重要**: 文字列のプレースホルダー部分の **{your\_username}** と **{your\_password\_here}** の値を、セットアップ時に指定したユーザー名とパスワードに変更します。

    ![パスワードの文字列のプレースホルダーには次の値が表示される: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "文字列のプレースホルダーの値")

8. [**保存**] をクリックします。

#### サブタスク 5: Visual Studio から eコマース Web アプリをデプロイする<a name="サブタスク-5:-Visual-Studio-から-eコマース-Web-アプリをデプロイする"></a>

1. Visual Studio の**ソリューション エクスプローラー**で **Web** フォルダーの **Contoso.Apps.SportsLeague.Web** プロジェクトに移動します。

    ![ソリューション エクスプローラーで Solution \'Contoso.Apps.SportsLeague\' (7 projects) の下にある Web フォルダーを展開した状態。その下の Contoso.Apps.SportsLeague.Web が選択されている](media/2019-04-19-14-03-04.png "ソリューション エクスプローラー")

2. **Contoso.Apps.SportsLeague.Web** プロジェクトを右クリックして [**発行**] を選択します。

    >**注**: 設定内容が構成に表示されていない場合は発行しないでください。Azure サブスクリプションに発行する場合は [**新しいプロファイル**] を選択します。
    > 
    > ![開発者が残した Visual Studio の発行構成。発行しないように指示するメッセージが示されている。[新しいプロファイル] リンクが囲まれている](media/2019-03-22-12-42-48.png "[新しいプロファイル] を選択")

3. 発行先に [**Azure App Service**] を選択し、[**既存のものを選択**] をクリックしてからウィザード最下部の [**プロファイルの作成**] をクリックします。

    ![[発行] タブで [Microsoft Azure App Service] タイル、[既存のものを選択] ラジオ ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image47.png "[発行] タブ")

4. ログオンを求めるメッセージが表示されたら、Azure サブスクリプションの資格情報でログオンします。

    ![App Service で [既存の App Service の選択] ダイアログが表示されている。サインイン リンクが強調表示されている](media/2019-04-19-14-07-19.png "Azure へのサインイン")

    >**注**: サインインしても何も起こらない場合は、Visual Studio をいったん終了してから再起動してソリューションを再度開きます。その後、再び発行手順を実行します。

5. **Contoso Sports Web App** を選択します (前の手順で指定した名前を使用します)。

    ![サブスクリプションの contososports の下にある contososportsweb0 が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image49.png "サブスクリプション")

6. [**OK**] を選択します。

7. [**発行**] をクリックして Web アプリケーションを発行します。

    >**注**: App Service の .NET Core 3.0.0 のサポートに関する警告が表示された場合、[**OK**] をクリックして無視します。
    >
    > ![App Service の .NET Core 3.0.0 のサポートに関する警告](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/2019-11-15-18-12-21.png "App Service の .NET Core 3.0.0 のサポートに関する警告")

8. Web アプリの発行が正常に完了したことを示すメッセージが Visual Studio の [**出力**] ビューに表示されます。

    ![Visual Studio の [出力] ビューのスクリーンショット。発行が成功したことを示すメッセージが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image50.png "Visual Studio の [出力] ビュー")

    >**注**: URL はグローバルに一意である必要があるため、スクリーンショットの出力とは異なる場合があります。

9. 新しい Web アプリケーションが新規ブラウザーで自動的に開きます。メニューの [ストア] リンクを選択して Web サイトを検証します。正常であれば商品アイテムが表示されます。商品データが取得されている場合は、データベースに正常に接続されています。

    ![[ストア] リンクのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image51.png "[ストア] リンク")

    >**トラブルシューティング**: Web サイトで商品が正常に表示されない場合、前の手順で入力した接続文字列、パスワード、Web アプリケーションの設定をすべて再確認します。

<!--
### Task 2: Setup SQL Database Geo-Replication

In this exercise, the attendee will provision a secondary SQL Database and configure Geo-Replication using the Microsoft Azure Portal.

#### Subtask 1: Add secondary database

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2. Select **SQL databases** in the navigation menu to the left, and select the name of the SQL Database you created previously.

    ![Screenshot of SQL Databases menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL Databases")

3. Under the **SETTINGS** menu area, select **Geo-Replication**.

    ![In the Settings section, Geo-Replication is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image53.png "Settings section")

4. Select the Azure Region to place the Secondary within.

    ![The Geo-Replication blade has a map of the world with locations marked on it. Under the map, Primary is set to West US, which on the map has a blue checkmark.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image54.png "Geo-Replication blade")

    The Secondary Azure Region should be the Region Pair for the region the SQL Database is hosted in. Consult <https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions> to see which region pair the location you are using for this lab is in.

    >**Note**: If you choose a region that cannot be used as a secondary region, you will not be able to pick a pricing plan. Choose another region.
    > 
    > ![Wrong geo-replication region selected. Not available options presented.](media/2019-03-30-16-05-25.png "Not available options presented.")

5. On the **Create secondary** blade, select **Secondary Type** as **Readable**.

6. Select **Target server** ***Configure required settings***.

    ![the Target server Configure required settings option is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image55.png "Target server option")

7. On the **New server** blade, specify the following configuration:

   - Server name: **A unique value (ensure the green checkmark appears)**.

   - Server admin login: **demouser**

   - Password and Confirm Password: **demo@pass123**

    ![The fields in the New Server blade display with the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image56.png "New Server blade")

8. Once the values are accepted in the **New server** blade, choose **Select**.

    ![Screenshot of the Select button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image20.png "Select button")

9. On the **Create secondary** blade, select **OK**.

    ![Screenshot of the OK button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image57.png "OK button")

    > **Note**: The Geo-Replication will take a few minutes to complete.

10. After the Geo-Replication has finished provisioning, select **SQL Databases** in the navigation menu to the left.

    ![The SQL databases option in the Azure Portal navigation menu](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL Databases")

11. Select the name of the Secondary SQL Database you just created.

    ![In the list of Databases, the ContosoSportsDB secondary replication role is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image58.png "Database list")

12. On the SQL database blade in the Essentials section, select the SQL Database Server name link.

    ![On the SQL database blade in the Essentials section, the Server name (contososqlserver2.database.windows.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image61.png "SQL database blade, Essentials section")

13. On the **SQL Server** blade, within the **Overview** pane, select **Show firewall settings** link.

    ![On the SQL Server blade, at the top, the Set server firewall tile is boxed in red.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image62.png "SQL Server blade, Essentials section")

14. On the **Firewall Settings** blade, specify a new rule named **ALL**, with START IP **0.0.0.0**, and END IP **255.255.255.255**.

    ![On the Firewall Settings blade, in the New rule section, a new rule has been created with the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "New rule section ")

    >**Note**: This is only done to make the lab easier to do. In production, you do **NOT** want to open your SQL Database to all IP Addresses this way. Instead, you will want to specify just the IP Addresses you wish to allow through the Firewall.

15. Select **Save**.

    ![Screenshot of the Firewall settings Save button.](media/2019-04-10-16-00-29.png "Firewall settings Save button")

16. Update progress can be found by choosing the **Notifications** link located at the top of the page.

    ![Screenshot of the Success dialog box, which says that the server firewall rules have been successfully updated.](media/2019-04-19-13-39-41.png "Success dialog box")

17. Close all configuration blades.

#### Subtask 2: Setup SQL Failover Group

With SQL Database Geo-Replication configured, the Azure SQL Failover Groups feature can be used to enable "auto failover" scenarios for the SQL Database. This enables a single connection string endpoint to be used by the application, and SQL Database will automatically handle failing over from Primary to Secondary database in the event of a SQL Database outage / down time.

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2. In the navigation menu to the left, select **SQL databases**, and select the name of the *primary* SQL Database you created previously.

    ![Screenshot of SQL Databases tile](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "Azure Portal")

3. On the **SQL database** blade, within the **Overview** pane, select the **Server name**.

    ![SQL database blade with server name highlighted](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/primarysqldatabaseserverlink.png "SQL database blade with server name highlighted")

4. On the **SQL server** blade, select **Failover groups** under **Settings**.

    ![Failover groups setting option](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlserverfailovergroupslink.png "Failover groups setting option")

5. On the **Failover groups** pane, select the **Add group** button.

    ![Add group button](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/failovergroupsaddgroupbutton.png "Add group buton")

6. On the **Failover group** pane, enter a unique **Failover group name**.

    ![Failover group name field](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupname.png "Failover group name field")

7. Select **Secondary server**, then choose the **Secondary SQL Database** that was previously created.

    ![Secondary SQL Database is highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailoversecondaryserver.png "Secondary SQL Database is highlighted")

8. Select **Database within the group**, then choose the **ContosoSportsDB** database, then click **Select**.

    ![Steps to choose the ContosoSportsDB are highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailoversecondarydatabase.png "Steps to choose the ContosoSportsDB are highlighted")

9. Select **Create** to create the SQL Failover Group.

10. Once the Failover Group has been created, select it in the list.

    ![Failover Group is highlighted](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergrouplist.png "Failover Group is highlighted")

11. Notice, on the **Failover group** pane, the map and display showing the _Primary_ and _Secondary_ SQL Database servers within the failover group. The _Primary_ database shows as **Automatic** failover for Read/Write of data, while the _Secondary_ database doesn't since it is currently Read only.

    ![Map display of Primary and Seconary databases.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupmap.png "Map display of Primary and Seconary databases")

12. Scroll down, below the map, to where the **Read/write listener endpoint** and **Read-only listener endpoint** are displayed. These allow for applications to be configured to connect to the SQL Failover Group endpoints instead of the individual SQL Server endpoints.

    Copy both **Listener Endpoint** values for later reference.

    ![Read/Write and Read-only listener endpoints are displayed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupendpoints.png "Read/Write and Read-only listener endpoints are displayed")

13. Go back to the **contososports** resource group blade.

14. Select the **contosoapp** web app (**App Service** type).

    ![contosoapp is highlighted](media/2019-04-19-13-46-40.png "contosoapp is highlighted")

15. On the **App Service** blade, scroll down in the left pane. Under the **Settings** menu, select **Configuration**.

    ![Configuration option is highlighted.](media/2019-04-19-16-38-54.png "Configuration option is highlighted")

16. Locate the **Connection Strings** section, and modify the value of the **ContosoSportsLeague** connection string to include the **Azure SQL Failover Group Read/Write Listener Endpoint** that was copied previously.

    > Note: The connection string will need to be in the following format:
    > ```
    > Server=tcp:{failover_group_endpoint};Initial Catalog=ContosoSportsDB;Persist Security Info=False;User ID={your_username};Password={your_password_here};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
    > ```
    >
    > Be sure to replace the string placeholder values **{your_username}**, **{your_password_here}**, and **{failover_group_endpoint}** with the username, password, and read/write listener endpoint for the SQL Database Failover Group. The username and password will remain the same as they were for the SQL Server.

17. Select **Save**.

#### Subtask 3: Failover SQL Database Failover Group

>**Note**: This subtask is optional.

Since the Replication and Failover process can take anywhere from 10 to 30 minutes to complete, you have the choice to skip Subtask 3 and 4, and go directly to Task 3. However, if you have the time, it is recommended that you complete these steps.

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2. In the navigation menu to the left, select **SQL databases**, and select the name of the *primary* SQL Database you created previously.

    ![Screenshot of SQL Databases tile.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "Azure Portal")

3. On the **Overview** pane, select the **Server name**.

    ![Server name is highlighted.](images/2020-03-17-19-35-23.png "Server name is highlighted")

4. On the **SQL server** blade, select **Failover groups** under Settings.

    ![Failover groups option is highlighted.](images/2020-03-17-19-37-00.png "Failover groups option is highlighted")

5. Select the **Failover group** in the list.

    ![Failover group is highlighted in the list.](images/2020-03-17-19-38-01.png "Failover group is highlighted in the list")

6. On the Failover group blade, select the **Forced Failover** button, then select **Yes** to confirm the forced failover of the SQL Database Failover Group.

    ![Forced failover confirmation is displayed.](images/2020-03-17-19-39-56.png "Forced failover confirmation is displayed")

The failover may take a few minutes to complete. You can continue with the next Subtask.

#### Subtask 4: Test e-commerce Web App after Failover

1. From the Azure portal, select **Resource Groups**, and select **contososports**.

2. Select the **Web App** created earlier.

3. On the **App Service** blade, select **Overview**.

    ![Screenshot of Overview menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image71.png "App Service blade")

4. On the **Overview** pane, select the **URL** for the Web App to open it in a new browser tab.

    ![On the App Service blade, in the Essentials section, the URL (http;//contososportsweb4azurewebsites.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image72.png "App Service blade Essentials section")

5. After the e-commerce Web App loads in Internet Explorer, select **STORE** in the top navigation bar of the website.

    ![On the Contoso sports league website navigation bar, the Store button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image73.png "Contoso sports league website navigation bar")

6. Verify the product list from the database displays.

    ![Screenshot of the Contoso store webpage. Under Team Apparel, a Contoso hat, tank top, and hoodie display.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image74.png "Contoso store webpage")

-->
### タスク 2: SQL Database の geo レプリケーションをセットアップする<a name="タスク-2:-SQL-Database-の-geo-レプリケーションをセットアップする"></a>

この演習では、セッション参加者が Azure Portal からセカンダリ SQL Database のプロビジョニングと geo レプリケーションの構成を行います。

#### サブタスク 1: セカンダリ データベースを追加する<a name="サブタスク-1:-セカンダリ-データベースを追加する"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. 左側のナビゲーション メニューで [**SQL データベース**] をクリックし、前の手順で作成した SQL Database の名前を選択します。

    ![[SQL データベース] メニュー オプションのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL データベース")

3. [**設定**] メニューで [**geo レプリケーション**] を選択します。

    ![[設定] セクションで [geo レプリケーション] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image53.png "[設定] セクション")

4. セカンダリ データベースを設置する Azure リージョンを選択します。

    ![[geo レプリケーション] ブレードには各リージョンの場所を示す世界地図が表示される。この地図では、プライマリは青のチェックマークで示された米国西部に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image54.png "[geo レプリケーション] ブレード")

    セカンダリを設置する Azure リージョンには、SQL Database がホストされているリージョンのリージョン ペアを選択します。このラボで使用するリージョン ペアの場所については <https://docs.microsoft.com/ja-jp/azure/best-practices-availability-paired-regions> を参照してください。

    >**注**: セカンダリ リージョンとして使用できないリージョンを選択した場合、料金プランが表示されません。他のリージョンを選択してください。
    > 
    > ![geo レプリケーション先のリージョンの選択が不正。使用不可のオプションが表示されている](media/2019-03-30-16-05-25.png "使用不可のオプションが表示されている")

5. [**セカンダリの作成**] ブレードで [**セカンダリの種類**] を [**読み取り可能**] に設定します。

6. [**ターゲット サーバー** - ***必要な設定の構成***] を選択します。

    ![[ターゲット サーバー - 必要な設定の構成] 設定オプションが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image55.png "[ターゲット サーバー] オプション")

7. [**新しいサーバー**] ブレードで次の構成を指定します。

   - サーバー名: **一意の値 (緑色のチェックマークが表示されることを確認)**

   - サーバー管理者ログイン: **demouser**

   - パスワード、およびパスワードの確認: **demo@pass123**

    ![前の手順で定義した設定が [新しいサーバー] ブレードのフィールドに表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image56.png "[新しいサーバー] ブレード")

8. [**新しいサーバー**] ブレードで値が承認されたら、[**選択**] をクリックします。

    ![[選択] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image20.png "[選択] ボタン")

9. [**セカンダリの作成**] ブレードで [**OK**] をクリックします。

    ![[OK] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image57.png "[OK] ボタン")

    > **注**: geo レプリケーションは完了までに数分程度かかります。

10. geo レプリケーションのプロビジョニングが完了したら、左側のナビゲーション メニューで [**SQL データベース**] を選択します。

    ![Azure Portal のナビゲーション メニューの [SQL データベース] オプション](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL データベース")

11. 前の手順で作成したセカンダリ SQL Database の名前を選択します。

    ![データベースのリストの中からセカンダリ レプリケーション ロールとして ContosoSportsDB を選択](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image58.png "データベース リスト")

12. [概要] セクションの [SQL データベース] ブレードで SQL Database サーバー名のリンクを選択します。

    ![[概要] セクションの [SQL データベース] ブレードでサーバー名 (contososqlserver2.database.windows.net) のリンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image61.png "[概要] セクションの [SQL データベース] ブレード")

13. [**SQL Server**] ブレードの [**概要**] ウィンドウで [**ファイアウォール設定の表示**] リンクを選択します。

    ![[SQL Server] ブレード上部の [ファイアウォール設定の表示] タイルが赤で囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image62.png "[概要] セクションの [SQL Server] ブレード")

14. [**ファイアウォール設定**] ブレードで、名称が **ALL**、開始 IP が **0.0.0.0**、終了 IP が **255.255.255.255** のルールを新規作成します。

    ![[ファイアウォール設定] ブレードの [新しいルール] セクションで前述の設定の新規ルールが作成されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "[新しいルール] セクション")

    >**注**: このラボでは、わかりやすいようにこのような設定にします。運用環境では、この例のようにすべての IP アドレスから SQL Database へのアクセスを許可する設定は**適切ではありません**。ファイアウォールの通過を許可する IP アドレスのみを指定してください。

15. [**保存**] をクリックします。

    ![ファイアウォール設定の [保存] ボタンのスクリーンショット](media/2019-04-10-16-00-29.png "ファイアウォール設定の [保存] ボタン")

16. ページ上部の [**通知**] リンクをクリックすると、更新の進捗状況を確認できます。

    ![サーバーのファイアウォール規則が正常に更新されたことを示すダイアログ ボックス](media/2019-04-19-13-39-41.png "更新成功を示すダイアログ ボックス")

17. 構成ブレードをすべて閉じます。

#### サブタスク 2: SQL フェールオーバー グループをセットアップする<a name="サブタスク-2:-SQL-フェールオーバー-グループをセットアップする"></a>

SQL Database の geo レプリケーションを構成すると、Azure SQL フェールオーバー グループ機能で SQL Database を「自動フェールオーバー」できます。この機能では、SQL Database で障害やサービス停止が発生した場合に、アプリケーションが単一の接続文字列エンドポイントを使用して SQL Database をプライマリ データベースからセカンダリ データベースに自動的にフェールオーバーします。

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. 左側のナビゲーション メニューで [**SQL データベース**] をクリックし、前の手順で作成した*プライマリ* SQL Database の名前を選択します。

    ![[SQL データベース] タイルのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "Azure Portal")

3. [**SQL データベース**] ブレードの [**概要**] ウィンドウで**サーバー名**を選択します。

    ![[SQL データベース] ブレードでサーバー名が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/primarysqldatabaseserverlink.png "[SQL データベース] ブレードでサーバー名が強調表示されている")

4. [**SQL Server**] ブレードで [**設定**]、[**フェールオーバー グループ**] の順に選択します。

    ![フェールオーバー グループ設定オプション](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlserverfailovergroupslink.png "フェールオーバー グループ設定オプション")

5. [**フェールオーバー グループ**] ウィンドウで [**グループの追加**] ボタンをクリックします。

    ![[グループの追加] ボタン](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/failovergroupsaddgroupbutton.png "[グループの追加] ボタン")

6. [**フェールオーバー グループ**] ウィンドウで一意の**フェールオーバー グループ名**を入力します。

    ![[フェールオーバー グループ名] フィールド](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupname.png "[フェールオーバー グループ名] フィールド")

7. [**セカンダリ サーバー**] をクリックし、前の手順で作成した**セカンダリ SQL Database** を選択します。

    ![セカンダリ SQL Database が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailoversecondaryserver.png "セカンダリ SQL Database が強調表示されている")

8. [**グループ内のデータベース**] をクリックし **ContosoSportsDB** データベースを選択してから [**選択**] をクリックします。

    ![ContosoSportsDB を選択する手順が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailoversecondarydatabase.png "ContosoSportsDB を選択する手順が強調表示されている")

9. [**作成**] をクリックして SQL フェールオーバー グループを作成します。

10. フェールオーバー グループが作成されたら、そのグループをリストから選択します。

    ![フェールオーバー グループが強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergrouplist.png "フェールオーバー グループが強調表示されている")

11. [**フェールオーバー グループ**] ウィンドウでは、地図上にフェールオーバー グループ内のプライマリとセカンダリの SQL Database サーバーの場所が表示されます。プライマリ データベースはデータの読み取り/書き込みの**自動**フェールオーバー対象として表示されます。セカンダリ データベースはこの時点では読み取り専用であるため、対象にはなりません。

    ![プライマリとセカンダリのデータベースの場所を示す地図](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupmap.png "プライマリとセカンダリのデータベースの場所を示す地図")

12. 下方向にスクロールすると、地図の下に [**読み取り/書き込みリスナー エンドポイント**] と [**読み取り専用リスナー エンドポイント**] が表示されます。これにより、アプリケーションからエンドポイントへの接続先として、個々の SQL Server エンドポイントではなく SQL フェールオーバー グループを構成できます。

    後で使用するため、両方の**リスナー エンドポイント**の値をメモしておきます。

    ![読み取り/書き込みエンドポイントと読み取り専用エンドポイントが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/sqlfailovergroupendpoints.png "読み取り/書き込みエンドポイントと読み取り専用エンドポイントが表示されている")

13. **contososports** リソース グループ ブレードに戻ります。

14. **contosoapp** Web アプリ (種類は **App Service**) を選択します。

    ![contosoapp が強調表示されている](media/2019-04-19-13-46-40.png "contosoapp が強調表示されている")

15. [**App Service**] ブレードの左側のウィンドウを下方向にスクロールします。[**設定**] メニューで [**構成**] をクリックします。

    ![[構成] オプションが強調表示されている](media/2019-04-19-16-38-54.png "[構成] オプションが強調表示されている")

16. [**接続文字列**] セクションに移動し、**ContosoSportsLeague** 接続文字列の値を、前の手順でメモを取った **Azure SQL フェールオーバー グループの読み取り/書き込みリスナー エンドポイント**に変更します。

    > 注: 接続文字列の書式は、以下のとおりです。
    > ```
    > Server=tcp:{failover_group_endpoint};Initial Catalog=ContosoSportsDB;Persist Security Info=False;User ID={your_username};Password={your_password_here};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
    > ```
    >
    > 文字列のプレースホルダーの **{your_username}**、**{your_password_here}**、**{failover_group_endpoint}** の部分の値をユーザー名、パスワード、SQL Database フェールオーバー グループの読み取り/書き込みリスナー エンドポイントに変更します。ユーザー名とパスワードは SQL Server 作成時と同じものを使用します。

17. [**保存**] をクリックします。

#### サブタスク 3: SQL Database フェールオーバー グループのフェールオーバーを実行する<a name="サブタスク-3:-SQL-Database-フェールオーバー-グループのフェールオーバーを実行する"></a>

>**注**: このサブタスクはオプションです。

レプリケーションとフェールオーバーの処理には 10 ～ 30 分程度かかります。サブタスク 3 および 4 は省略してタスク 3 に直接進んでもかまいません。ただし、時間に余裕があればこれらの手順も習得することをおすすめします。

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. 左側のナビゲーション メニューで [**SQL データベース**] をクリックし、前の手順で作成した*プライマリ* SQL Database の名前を選択します。

    ![[SQL Databases] タイルのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "Azure Portal")

3. [**概要**] ウィンドウで**サーバー名**を選択します。

    ![サーバー名が強調表示されている](images/2020-03-17-19-35-23.png "サーバー名が強調表示されている")

4. [**SQL Server**] ブレードで [**設定**]、[**フェールオーバー グループ**] の順に選択します。

    ![[フェールオーバー グループ] オプションが強調表示されている](images/2020-03-17-19-37-00.png "[フェールオーバー グループ] オプションが強調表示されている")

5. リストから**フェールオーバー グループ**を選択します。

    ![リスト内のフェールオーバー グループが強調表示されている](images/2020-03-17-19-38-01.png "リスト内のフェールオーバー グループが強調表示されている")

6. [フェールオーバー グループ] ブレードで [**強制フェールオーバー**] ボタン、[**はい**] の順にクリックして SQL Database フェールオーバー グループの強制フェールオーバーを設定することを確認します。

    ![強制フェールオーバーの確認画面](images/2020-03-17-19-39-56.png "強制フェールオーバーの確認画面")

フェールオーバーは完了までに数分程度かかります。その間に次のサブタスクに進みます。

#### サブタスク 4: フェールオーバー後に eコマース Web アプリをテストする<a name="サブタスク-4:-フェールオーバー後に-eコマース-Web-アプリをテストする"></a>

1. Azure Portal で [**リソース グループ**] をクリックし、**contososports** を選択します。

2. 前の手順で作成した **Web アプリ**を選択します。

3. [**App Service**] ブレードで [**概要**] を選択します。

    ![[概要] メニュー オプションのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image71.png "[App Service] ブレード")

4. [**概要**] ウィンドウで Web アプリの **URL** を選択し、ブラウザーの新規タブで開きます。

    ![[App Service] ブレードの [概要] セクションの URL (http;//contososportsweb4azurewebsites.net) リンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image72.png "[App Service] ブレードの [概要] セクション")

5. Internet Explorer に eコマース Web アプリが 読み込まれたら、Web サイトのナビゲーション バーで [**ストア**] を選択します。

    ![Contoso Sports League の Web サイトのナビゲーション バーの [ストア] ボタンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image73.png "Contoso Sports League の Web サイトのナビゲーション バー")

6. データベースから取得された製品リストが表示されることを確認します。

    ![Contoso ストアの Web ページのスクリーンショット。チーム ウェアの項目に Contoso の帽子、タンクトップ、パーカーが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image74.png "Contoso ストアの Web ページ")

<!--
### Task 3: Deploying the Call Center admin website

In this exercise, you will provision a website via the Azure Web App template using the Microsoft Azure Portal. You will then edit the necessary configuration files in the Starter Project and deploy the call center admin website.

#### Subtask 1: Provision the call center admin Web App

1. Using a new tab or instance of your browser, navigate to the Azure Management portal <http://portal.azure.com>.

2. Select **+Create a resource** then select **Web**, then **Web App**.

3. Specify a **unique URL** for the Web App, **resource group** you have used throughout the lab are selected. Also, specify **.NET Core 3.1 (LTS)** as the **Runtime stack**.

    ![On the Web App blade, the App name field is set to contososportscallcentercp.](media/2019-03-28-05-29-59.png "Web App blade")

4. Select **Linux Plan**, and create a new Linux-based App Service Plan for the Web App.

5. After the values are accepted, select **Review and create**, then **Create**.  It will take a few minutes to provision.

#### Subtask 2: Update the configuration in the starter project

1. Navigate to the **App Service** blade for the Call Center Admin App just provisioned.

    ![The App Service blade displays.](media/2020-03-17-19-59-03.png "App Service blade")

2. On the **App Service** blade, select **Configuration** in the left pane.

    ![In the App Service blade, under Settings, select Configuration link.](media/2019-04-19-16-38-54.png "Configuration link")

3. Scroll down, and locate the **Connection strings** section.

4. Add a new **Connection string** with the following values:

    - Name: `ContosoSportsLeague`

    - Value: **Enter the Connection String for the SQL Database Failover Group Read/Write Listener Endpoint**.

    - Type: `SQL Azure`

    ![The Connection Strings fields display the previously defined values.](media/2019-04-11-04-31-51.png "Connection Strings fields")

5. Select the **Update** button.

6. Select the **Save** button.

    ![the Save button is circled on the App Service blade.](media/2019-03-28-05-36-38.png "App Service blade")

#### Subtask 3: Deploy the call center admin Web App from Visual Studio

1. Navigate to the **Contoso.Apps.SportsLeague.Admin** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

2. Right-click the **Contoso.Apps.SportsLeague.Admin** project, and select **Publish**.

    ![In Solution Explorer, the right-click menu for Contoso.Apps.SportsLeague.Admin displays, and Publish is selected.](media/2019-04-19-14-30-03.png "Right-Click menu")

3. Choose **App Service Linux** as the publish target, choose **Select Existing**, then select **Create Profile**.

    ![On the Publish tab, App Service Linux is selected. Below that, the radio button is selected for Select Existing.](media/2020-03-17-20-09-01.png "Publish tab")

4. Select the **Web App** for the Call Center Admin App.

    ![In the App Service section, in the tree view at the bottom, the contososports folder is expanded, and the Call Center Web App is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image88.png "App Service section")

5. Select **OK**.

6. Select **Publish**.

    ![Display the Visual Studio Contoso.Apps.SportsLeague.Admin publish success message in the output.](media/2019-03-28-05-45-28.png "Publish Succeeded")

6. Once deployment is complete, navigate to the Web App. It should look like the following:

    ![The Contoso website displays the Contoso Sports League Admin webpage, which says that orders that display below are sorted by date, and you can select an order to see its details. However, at this time, there is no data available under Completed Orders.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image89.png "Contoso website")

-->
### タスク 3: コール センター管理 Web サイトをデプロイする<a name="タスク-3:-コール-センター管理-Web-サイトをデプロイする"></a>

この演習では、Azure Web アプリ テンプレートを使用して Azure Portal から Web サイトをプロビジョニングします。その後、スターター プロジェクト内の構成ファイル群を必要に応じて編集し、コール センター管理 Web サイトをデプロイします。

#### サブタスク 1: コール センター管理 Web アプリをプロビジョニングする<a name="サブタスク-1:-コール-センター管理-Web-アプリをプロビジョニングする"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. [**+リソースの作成**]、[**Web**]、[**Web アプリ**] の順に選択します。

3. Web アプリの**一意の URL** を指定し、このラボで使用している**リソース グループ**を選択します。[**ランタイム スタック**] には **.NET Core 3.1 (LTS)** を指定します。

    ![[Web アプリ] ブレードのアプリ名フィールドが contososportscallcenterapp に設定されている](media/2019-03-28-05-29-59.png "[Web アプリ] ブレード")

4. [**Linux プラン**] を選択し、Web アプリ用の Linux ベースの App Service プランを新規作成します。

5. 値が承認されたら [**確認と作成**]、[**作成**] の順にクリックします。  プロビジョニングには数分程度かかります。

#### サブタスク 2: スターター プロジェクトの構成を更新する<a name="サブタスク-2:-スターター-プロジェクトの構成を更新する"></a>

1. 前の手順でプロビジョニングしたコール センター管理アプリの [**App Service**] ブレードに移動します。

    ![[App Service] ブレードの表示](media/2020-03-17-19-59-03.png "[App Service] ブレード")

2. [**App Service**] ブレードの左側のウィンドウで [**構成**] を選択します。

    ![[App Service] ブレードの [設定] で [構成] リンクをクリック](media/2019-04-19-16-38-54.png "[構成] リンク")

3. 下方向にスクロールして [**接続文字列**] セクションに移動します。

4. **接続文字列**を新規追加し、以下の値を指定します。

    - 名前: `ContosoSportsLeague`

    - 値: **SQL Database フェールオーバー グループの読み取り/書き込みリスナー エンドポイント**の接続文字列を入力します。

    - 種類: `SQL Azure`

    ![[接続文字列] フィールドに前の手順で定義した値が表示されている](media/2019-04-11-04-31-51.png "[接続文字列] フィールド")

5. [**更新**] ボタンをクリックします。

6. [**保存**] ボタンをクリックします。

    ![[App Service] ブレードの [保存] ボタンが囲まれている](media/2019-03-28-05-36-38.png "[App Service] ブレード")

#### サブタスク 3: Visual Studio からコール センター管理 Web アプリをデプロイする<a name="サブタスク-3:-Visual-Studio-からコール-センター管理-Web-アプリをデプロイする"></a>

1. Visual Studio の**ソリューション エクスプローラー**で **Web** フォルダーの **Contoso.Apps.SportsLeague.Admin** プロジェクトに移動します。

2. **Contoso.Apps.SportsLeague.Admin** プロジェクトを右クリックして [**発行**] を選択します。

    ![ソリューション エクスプローラーで Contoso.Apps.SportsLeague.Admin のメニューを右クリックした様子。[発行] が選択されている](media/2019-04-19-14-30-03.png "右クリック メニュー")

3. 発行先に [**App Service Linux**] を指定し、[**既存のものを選択**]、[**プロファイルの作成**] を選択します。

    ![[発行] タブで [App Service Linux] が選択されている。その下で [既存のものを選択] ラジオボタンが選択されている](media/2020-03-17-20-09-01.png "[発行] タブ")

4. コール センター管理アプリの **Web アプリ**を選択します。

    ![[App Service] セクションのツリー ビュー下部に contososports フォルダーが展開されていて、コール センター Web アプリが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image88.png "[App Service] セクション")

5. [**OK**] を選択します。

6. [**発行**] をクリックします。

    ![Visual Studio の出力画面に Contoso.Apps.SportsLeague.Admin の発行が成功したことを示すメッセージが表示されている](media/2019-03-28-05-45-28.png "発行成功")

7. デプロイが完了したら Web アプリに移動します。以下のような内容が表示されます。

    ![Contoso の Web サイトに Contoso Sports League 管理 Web ページが表示されている。下部の注文表示欄は日付順に並び、各注文を選択すると詳細が表示される。ただし、現時点では「Completed Orders」の下の注文にはデータが含まれていない](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image89.png "Contoso の Web サイト")

<!--
### Task 4: Deploying the payment gateway

In this exercise, the attendee will provision an Azure API app template using the Microsoft Azure Portal. The attendee will then deploy the payment gateway API to the API app.

#### Subtask 1: Provision the payment gateway API app

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2. Select **+Create a resource**, type **API App** into the marketplace search box, and press **Enter**.  Select the **Create** button.

    ![In the Azure Portal left menu, New is selected. In the New blade, the search field is set to API App.](media/2019-03-28-07-57-54.png "Azure Portal - Create API App")

3. On the new **API App** blade, create the following values:

   - **App name:** Specify a unique name for the App Name.
   - **Subscription:** Your Azure MSDN subscription.
   - **Resource Group:** Select **Use existing** option.
   - **App Service Plan/Location** Select the same primary region used in previous steps.
   - **Application Insights:** **Disabled**

    ![On the API App blade. Configuration fields are displayed.](media/2019-04-20-14-55-42.png "Configuration fields are displayed")

4. After the values are accepted, select **Create**.  It will take a few minutes to provision.

#### Subtask 2: Deploy the Contoso.Apps.PaymentGateway project in Visual Studio

1. Navigate to the **Contoso.Apps.PaymentGateway** project located in the **APIs** folder using the **Solution Explorer** in Visual Studio.

2. Right-click the **Contoso.Apps.PaymentGateway** project, and select **Publish**.

    ![In Solution Explorer, Contoso.Apps.PaymentGateway is selected, and in its right-click menu, Publish is selected.](media/2019-04-19-14-52-22.png "Solution Explorer")

3. On the **Publish Web** dialog box, select **Azure App Service**, then choose **Select Existing**, and **Create Profile**.

    > **Note**: If your Azure resource group does not show, choose **New Profile**.

4. Select the Payment Gateway API app created earlier, select **OK**.

    ![In the App Service section, the contososports folder is expanded, and PaymentsAPIO is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image98.png "App Service section")

5. Select **Publish**.

6. In the Visual Studio **Output** view, you will see a status indicating the Web App was published successfully.

    ![The Visual Studio output shows that the web app was published successfully.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image99.png "Visual Studio output")

7. Copy and paste the gateway **URL** of the deployed **API App** into Notepad for later use.

8. Viewing the Web App in a browser will display the Swagger UI for the API.

   ![Payment Gateway is up and running and the Swagger UI is displayed.](media/2019-04-11-04-58-04.png "Swagger UI")

-->
### タスク 4: 支払いゲートウェイをデプロイする<a name="タスク-4:-支払いゲートウェイをデプロイする"></a>

この演習では、セッション参加者が Azure Portal から Azure API アプリ テンプレートをプロビジョニングします。その後、支払いゲートウェイ API を API アプリにデプロイします。

#### サブタスク 1: 支払いゲートウェイ API アプリをプロビジョニングする<a name="サブタスク-1:-支払いゲートウェイ-API-アプリをプロビジョニングする"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. [**+リソースの作成**] を選択し、マーケットプレースの検索ボックスに「**API App**」と入力して **Enter** キーを押します。  [**作成**] ボタンをクリックします。

    ![Azure Portal の左側のメニューで [新規作成] が選択されている。[新規作成] ブレードの検索フィールドに「API App」と入力されている](media/2019-03-28-07-57-54.png "Azure Portal - API アプリの作成")

3. 新規作成した **API アプリ**のブレードで以下の値を指定します。

   - **アプリ名**: アプリケーションの一意の名前を指定します。
   - **サブスクリプション**: 自身の Azure MSDN サブスクリプションを指定します。
   - **リソース グループ**: [**既存のものを使用**] オプションを選択します。
   - **App Service プラン/場所**: 前の手順で指定したプライマリ リージョンと同じリージョンを指定します。
   - **Application Insights**: [**無効にする**] を選択します。

    ![API アプリのブレードの構成フィールドが表示されている](media/2019-04-20-14-55-42.png "構成フィールドの表示")

4. 値が承認されたら [**作成**] をクリックします。  プロビジョニングには数分程度かかります。

#### サブタスク 2: Visual Studio から Contoso.Apps.PaymentGateway プロジェクトをデプロイする<a name="サブタスク-2:-Visual-Studio-から-Contoso.Apps.PaymentGateway-プロジェクトをデプロイする"></a>

1. Visual Studio の**ソリューション エクスプローラー**で **API** フォルダーの **Contoso.Apps.PaymentGateway** プロジェクトに移動します。

2. **Contoso.Apps.PaymentGateway** プロジェクトを右クリックして [**発行**] を選択します。

    ![ソリューション エクスプローラーで Contoso.Apps.PaymentGateway が選択され、右クリック メニューで [発行] が選択されている](media/2019-04-19-14-52-22.png "ソリューション エクスプローラー")

3. [**Web の発行**] ダイアログ ボックスで [**Azure App Service**]、[**既存のものを選択**]、[**プロファイルの作成**] の順に選択します。

    > **注**: Azure リソース グループが表示されていない場合、[**新しいプロファイル**] を選択します。

4. 前の手順で作成した支払いゲートウェイ API アプリを選択し、[**OK**] をクリックします。

    ![[App Service] セクションで contososports フォルダーが展開されていて、PaymentsAPIO が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image98.png "[App Service] セクション")

5. [**発行**] をクリックします。

6. Web アプリの発行が正常に完了したことを示すメッセージが Visual Studio の [**出力**] ビューに表示されます。

    ![Visual Studio の出力で Web アプリが正常に発行されたことが示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image99.png "Visual Studio の出力")

7. 後で使用するため、デプロイした **API アプリ**のゲートウェイの **URL** をメモしておきます。

8. ブラウザーで Web アプリを開くと、API の Swagger UI が表示されます。

   ![支払いゲートウェイが稼働を開始し Swagger UI が表示されている](media/2019-04-11-04-58-04.png "Swagger UI")

<!--
### Task 5: Deploying the Offers Web API

In this exercise, the attendee will provision an Azure API app template using the Microsoft Azure Portal. The attendee will then deploy the Offers Web API.

#### Subtask 1: Provision the Offers Web API app

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal (<http://portal.azure.com>).

2. Select **+Create a resource**, type **API App** into the marketplace search box, and press **Enter**.  Select the **Create** button.

3. On the new **API App** blade, specify a unique name for the **API App**, and ensure the previously used Resource Group and App Service Plan are selected.

    ![In the API App blade, offersapith is typed in the App name field. App configuration fields displayed.](media/2019-04-11-05-03-33.png "API App blade")

4. After the values are accepted, select the **Create** button.

5. When the Web App template has completed provisioning, open the new API App by, in the navigation menu to the left, select **App Services** and then the Offer API app you just created.

   ![In the Azure Portal, on the left More services is selected, and on the right under Web + Mobile, App Services displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image101.png "Azure Portal, More Services")

#### Subtask 2: Configure Cross-Origin Resource Sharing (CORS)

1. On the **App Service** blade for the Offers API, under the **API** menu section, scroll down and select **CORS**.

    ![In the App Service blade, under API, CORS is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image102.png "App Service blade")

2. In the **Allowed Origins** text box, specify `*` to allow all origins, and select **Save**.

    >**Note**: You should not normally do this in a production environment. In production, you should enter the specific domains as allowed origins you need to allow CORS access to the API. The wildcard (*) is used for this lab to make it easier just for this lab.

    ![CORS configuration blade displayed.  Entering * as the Allowed Origins value.](media/2019-03-28-08-20-57.png "CORS configuration blade")

#### Subtask 3: Update the configuration in the starter project

1. On the **App Service** blade for the Offers API, select **Configuration**.

    ![In the App Service blade, under Settings, select Configuration link.](media/2019-04-19-16-38-54.png "Configuration link")

2. In the **Connection Strings** section, add a new **Connection string** with the following values:

      - Name: `ContosoSportsLeague`

      - Value: **Enter the Connection String for the SQL Database Failover Group Read-only Listener Endpoint**.

      - Type: `SQL Azure`

        ![The Connection Strings fields display the previously defined values.](media/2019-04-11-04-31-51.png "Connection Strings fields")

        >**Note**: The Connection String for the SQL Database Failover Group Read-only Listener Endpoint will be in the following format:
        >
        > ```
        > Server=tcp:{failover_group_endpoint};Initial Catalog=ContosoSportsDB;Persist Security Info=False;User ID={your_username};Password={your_password_here};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
        > ```
        >
        > Ensure you replace the string placeholder values **{your\_username}**, **{your\_password\_here}**, and **{failover_group_endpoint}** with the username, password, and Failover Group Read-only Listener Endpoint you respectively setup during creation (demouser & demo@pass123).
        >
        > ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder value")
        >
        > The SQL Failover Group Read-only Listener Endpoint will be the DNS name that ends in `.secondary.database.windows.net`. You will have copied this previously when setting up the SQL Failover Group.

3. Select the **Update** button.

4. Select the **Save** button.

    ![The Save button is circled on the App Service blade.](media/2019-03-28-05-36-38.png "App Service blade")

#### Subtask 4: Deploy the Contoso.Apps.SportsLeague.Offers project in Visual Studio

1. Navigate to the **Contoso.Apps.SportsLeague.Offers** project located in the **APIs** folder using the **Solution Explorer** in Visual Studio.

2. Right-click the **Contoso.Apps.SportsLeague.Offers** project, and select **Publish**.

    ![In Solution Explorer, from the Contoso.Apps.SportsLeague.Admin right-click menu, Publish is selected.](media/2019-04-19-15-03-45.png "Solution Explorer")

3. On the **Publish Web** dialog box, select **Azure App Service**, choose **Select Existing**, and select **Create Profile**.

    ![On the Publish tab, the Microsoft Azure App Service tile is selected, and under it, the radio button for Select Existing is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image109.png "Publish tab")

4. Select the Offers API app created earlier, and select **OK**.

    ![In the App Service section, the contososports folder is expanded, and OffersAPI4 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image110.png "App Service section")

5. Select **Publish**.

6. In the Visual Studio **Output** view, you will see a status the API app was published successfully.

7. Record the value of the deployed API app URL into Notepad for later use.

8. Viewing the Web App in a browser will display the Swagger UI for the API.

    ![Payment Gateway is up and running and the Swagger UI is displayed.](media/2019-04-11-05-20-40.png "Swagger UI")

9. Within the Swagger UI for the Offers API, select the `/api/get` method on the API. Then select the **Try it out** button, and then **Execute** to test out the API call from within the Swagger UI in the web browser. Once it executes, scroll down to view the results of the API call execution.

    ![Swagger UI displaying API call response.](media/2020-03-17-20-56-31.png "Swagger UI")

-->
### タスク 5: Offers Web API をデプロイする<a name="タスク-5:-Offers-Web-API-をデプロイする"></a>

この演習では、セッション参加者が Azure Portal から Azure API アプリ テンプレートをプロビジョニングします。その後、Offers Web API をデプロイします。

#### サブタスク 1: Offers Web API アプリをプロビジョニングする<a name="サブタスク-1:-Offers-Web-API-アプリをプロビジョニングする"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. [**+リソースの作成**] を選択し、マーケットプレースの検索ボックスに「**API App**」と入力して **Enter** キーを押します。  [**作成**] ボタンをクリックします。

3. 新規作成した **API アプリ**のブレードで、その **API アプリ**に一意の名前を指定します。また、前の手順で使用したリソース グループと App Service プランが選択されていることを確認します。

    ![API アプリのブレードでアプリ名として「offersapith」と入力されている。アプリの構成フィールドが表示されている](media/2019-04-11-05-03-33.png "API アプリのブレード")

4. 値が承認されたら [**作成**] ボタンをクリックします。

5. Web アプリのテンプレートのプロビジョニングが完了したら、左側のナビゲーション メニューの [**App Service**] をクリックし、前の手順で作成した Offers API アプリを選択して、新しい API アプリを開きます。

   ![Azure Portal 左側の [その他のサービス] が選択されていて、右下の [Web + モバイル] に [App Service] が表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image101.png "Azure Portal、その他のサービス")

#### サブタスク 2: クロス オリジン リソース共有 (CORS) を構成する<a name="サブタスク-2:-クロス-オリジン-リソース共有-(CORS)-を構成する"></a>

1. Offers API の [**App Service**] ブレードの [**API**] メニューを下方向にスクロールして、[**CORS**] を選択します。

    ![[App Service] ブレードの [API] で [CORS] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image102.png "[App Service] ブレード")

2. [**許可されたオリジン**] テキスト ボックスで `*` を指定してすべてのオリジンを許可し、[**保存**] をクリックします。

    >**注**: 通常、この設定は運用環境ではおすすめしません。運用環境では特定のドメインを入力し、API への CORS アクセスを許可する必要があるオリジンのみに限定します。このラボでは、わかりやすいようにワイルドカード (*) を使用します。

    ![CORS の構成ブレードが表示されている。  [許可されたオリジン] の値として * が入力されている](media/2019-03-28-08-20-57.png "CORS の構成ブレード")

#### サブタスク 3: スターター プロジェクトの構成を更新する<a name="サブタスク-3:-スターター-プロジェクトの構成を更新する"></a>

1. Offers API の [**App Service**] ブレードで [**構成**] を選択します。

    ![[App Service] ブレードの [設定] で [構成] リンクをクリック](media/2019-04-19-16-38-54.png "[構成] リンク")

2. [**接続文字列**] セクションで**接続文字列**を新規追加し、以下の値を指定します。

      - 名前: `ContosoSportsLeague`

      - 値: **SQL Database フェールオーバー グループの読み取り専用リスナー エンドポイント**の接続文字列を入力します。

      - 種類: `SQL Azure`

        ![[接続文字列] フィールドに前の手順で定義した値が表示されている](media/2019-04-11-04-31-51.png "[接続文字列] フィールド")

        >**注**: SQL Database フェールオーバー グループの読み取り専用リスナー エンドポイントの接続文字列の書式は、以下のとおりです。
        >
        > ```
        > Server=tcp:{failover_group_endpoint};Initial Catalog=ContosoSportsDB;Persist Security Info=False;User ID={your_username};Password={your_password_here};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
        > ```
        >
        > 文字列のプレースホルダー部分の **{your\_username}**、**{your\_password\_here}**、**{failover_group_endpoint}** の値を、セットアップ時に作成したユーザー名 (demouser)、パスワード (demo@pass123)、およびフェールオーバー グループの読み取り専用リスナー エンドポイントに変更します。
        >
        > ![パスワードの文字列のプレースホルダーには次の値が表示される: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "文字列のプレースホルダーの値")
        >
        > SQL フェールオーバー グループの読み取り専用リスナー エンドポイントは、`.secondary.database.windows.net` という文字列が末尾に付く DNS 名です。この値は、SQL フェールオーバー グループをセットアップしたときにコピーしたものです。

3. [**更新**] ボタンをクリックします。

4. [**保存**] ボタンをクリックします。

    ![[App Service] ブレードの [保存] ボタンが囲まれている](media/2019-03-28-05-36-38.png "[App Service] ブレード")

#### サブタスク 4: Visual Studio から Contoso.Apps.SportsLeague.Offers プロジェクトをデプロイする<a name="サブタスク-4:-Visual-Studio-から-Contoso.Apps.SportsLeague.Offers-プロジェクトをデプロイする"></a>

1. Visual Studio の**ソリューション エクスプローラー**で **API** フォルダーの **Contoso.Apps.SportsLeague.Offers** プロジェクトに移動します。

2. **Contoso.Apps.SportsLeague.Offers** プロジェクトを右クリックして [**発行**] を選択します。

    ![ソリューション エクスプローラーで Contoso.Apps.SportsLeague.Offers が選択されていて右クリック メニューで [発行] が選択されている](media/2019-04-19-15-03-45.png "ソリューション エクスプローラー")

3. [**Web の発行**] ダイアログ ボックスで [**Azure App Service**]、[**既存のものを選択**]、[**プロファイルの作成**] の順に選択します。

    ![[発行] タブで [Microsoft Azure App Service] タイル、[既存のものを選択] ラジオ ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image109.png "[発行] タブ")

4. 前の手順で作成した Offers API アプリを選択し、[**OK**] をクリックします。

    ![[App Service] セクションで contososports フォルダーが展開されていて OffersAPI4 が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image110.png "[App Service] セクション")

5. [**発行**] をクリックします。

6. API アプリの発行が正常に完了したことを示すメッセージが Visual Studio の [**出力**] ビューに表示されます。

7. 後で使用するため、デプロイされた API アプリの URL をメモしておきます。

8. ブラウザーで Web アプリを開くと、API の Swagger UI が表示されます。

    ![Offers API が稼働を開始し Swagger UI が表示されている](media/2019-04-11-05-20-40.png "Swagger UI")

9. Offers API の Swagger UI で、API の `/api/get` メソッドを選択します。続いて [**試してみる**] ボタン、[**実行**] の順に選択し、Web ブラウザーで Swagger UI 内部からの API 呼び出しをテストします。実行後、出力画面を下方向にスクロールして API 呼び出しの実行結果を確認します。

    ![Swagger UI で API 呼び出しの応答が表示されている](media/2020-03-17-20-56-31.png "Swagger UI")

<!--
### Task 6: Update and deploy the e-commerce website

#### Subtask 1: Update the Application Settings for the Web App that hosts the Contoso.Apps.SportsLeague.Web project

1. Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2. Select **Resource groups** then the **contososports** resource group.

3. Select the **App Service Web App** for the front-end web application.

    ![In the Resource Group blade on the right, under Name, contosoapp is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image113.png "Resource Group blade")

4. On the **App Service** blade, scroll down, and select **Configuration** in the left pane.

    ![In the App Service blade, under Settings, select Configuration link.](media/2019-04-19-16-38-54.png "Configuration link")

5. Scroll down, and locate the **Applications settings** section.

6. Add a new **Application Setting** with the following values:

   - App Setting Name: `paymentsAPIUrl`

   - Value: Enter the **HTTPS** URL for the Payments API App with `/api/nvp` appended to the end.

        >**Example**: `https://paymentsapi0.azurewebsites.net/api/nvp`

    ![In the Application settings section of the App Service blade, the previously defined application setting values are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image116.png "App settings")

7. Add another **Application Setting** with the following values:

   - App Setting Name: `offersAPIUrl`

   - Value: Enter the **HTTPS** URL for the Offers API App with `/api/get` appended to the end.

    >**Example**: `https://offersapi4.azurewebsites.net/api/get`

    ![In the Application settings section of the App Service blade, the previously defined application setting values are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image117.png "App settings section")

    >**Note**: Ensure both API URLs are using **SSL** (https://), or you will see a CORS errors.

8. Select **Save**.

#### Subtask 2: Validate App Settings are correct

1. On the **App Service** blade, select **Overview**.

    ![Overview is selected on the left side of the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image119.png "App Service blade")

2. In the **Overview** pane, select the **URL** for the Web App to open it in a new browser tab.

    ![On the right side of the App Service blade, under Essentials, the URL (http://contososportsweb2101.azurewebsites.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image120.png "App Service blade")

3. On the homepage, you should see the latest offers populated from the Offers API.

    ![On the Contoso Sports League webpage, Today\'s offers display: Baseball socks, Road bike, and baseball mitt.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image121.png "Contoso Sports League webpage")

4. Submit several test orders to ensure all pieces of the site are functional.  **Accept the default data during the payment processing.**

    ![On the Contoso Sports League webpage, the message Order Completed displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image122.png "Contoso Sports League webpage")

>**Leader Note**: If the attendee is still experiencing CORS errors, ensure the URLs to the Web App in Azure local host are exact.

-->
### タスク 6: eコマース Web サイトを更新してデプロイする<a name="タスク-6:-eコマース-Web-サイトを更新してデプロイする"></a>

#### サブタスク 1: Contoso.Apps.SportsLeague.Web プロジェクトをホストする Web アプリケーションの設定を更新する<a name="サブタスク-1:-Contoso.Apps.SportsLeague.Web-プロジェクトをホストする-Web-アプリケーションの設定を更新する"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. [**リソース グループ**]、**contososports** リソース グループの順に選択します。

3. フロントエンド Web アプリケーションとして **App Service Web アプリ**を選択します。

    ![右側の [リソース グループ] ブレードの [名前] で contosoapp が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image113.png "[リソース グループ] ブレード")

4. [**App Service**] ブレードを下方向にスクロールし、左側のウィンドウの [**構成**] を選択します。

    ![[App Service] ブレードの [設定] で [構成] リンクをクリック](media/2019-04-19-16-38-54.png "[構成] リンク")

5. 下方向にスクロールして [**アプリケーション設定**] セクションに移動します。

6. **アプリケーション設定**を新規追加し、以下の値を指定します。

   - アプリケーション設定名: `paymentsAPIUrl`

   - 値: `/api/nvp` という文字列が末尾に付く支払いゲートウェイ API アプリの **HTTPS** プロトコルの URL を入力します。

        >**例**: `https://paymentsapi0.azurewebsites.net/api/nvp`

    ![[App Service] ブレードの [アプリケーション設定] セクションで、前の手順で定義したアプリケーション設定の値が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image116.png "アプリケーション設定")

7. **アプリケーション設定**をもう 1 つ追加し、以下の値を指定します。

   - アプリケーション設定名: `offersAPIUrl`

   - 値: `/api/get` という文字列が末尾に付く Offers API アプリの **HTTPS** プロトコルの URL を入力します。

    >**例**: `https://offersapi4.azurewebsites.net/api/get`

    ![[App Service] ブレードの [アプリケーション設定] セクションで、前の手順で定義したアプリケーション設定の値が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image117.png "アプリケーション設定")

    >**注**: どちらの API の URL も **SSL** (https://) であることを確認します。SSL ではない場合、CORS エラーが発生します。

8. [**保存**] をクリックします。

#### サブタスク 2: アプリケーション設定が適切であることを検証する<a name="サブタスク-2:-アプリケーション設定が適切であることを検証する"></a>

1. [**App Service**] ブレードで [**概要**] を選択します。

    ![[App Service] ブレード左側で [概要] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image119.png "[**App Service**] ブレード")

2. [**概要**] ウィンドウで Web アプリの **URL** を選択し、ブラウザーの新規タブで開きます。

    ![[App Service] ブレード右側の [概要] で URL (http://contososportsweb2101.azurewebsites.net) リンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image120.png "[App Service] ブレード")

3. Offers API から提供される最新製品がホーム ページに表示されます。

    ![Contoso Sports League の Web ページに本日のおすすめが表示されている: 野球用ソックス、自転車、野球用グローブ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image121.png "Contoso Sports League の Web ページ")

4. サイト各部が正常に機能しているかテストするため、注文テストを複数回行います。  **支払い処理では既定のデータを承認します。**

    ![Contoso Sports League の Web ページに注文完了のメッセージが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image122.png "Contoso Sports League の Web ページ")

>**トレーナー向けメモ**: 参加者の CORS エラーが発生し続けている場合は、Azure ローカル ホストの Web アプリの URL が正しいかどうか確認します。

<!--
## Exercise 2: Identity and Security

Duration: 75 Minutes

The Contoso call center admin application will only be accessible by users of the Contoso Active Directory environment. You have been asked to create a new Azure AD Tenant and secure the application so only users from the tenant can log on.

### Task 1: Enable Azure AD Premium Trial

>**Note**: This task is **optional**, and it is valid only if you are a global administrator on the Azure AD tenant associated with your subscription.

1. Navigate to the Azure Management portal, [http://portal.azure.com](http://portal.azure.com/), using a new tab or instance.

2. In the left-hand navigation menu, select **Azure Active Directory**.

    ![The Azure Active Directory menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Portal")

3. On the **Azure Active Directory** blade, locate and select the **Company branding** option.

    ![In the Azure Active Directory blade, Company branding is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image124.png "Azure Active Directory blade")

4. In the right pane, select the **Get a free Premium trial...** link.

    ![On the left side of the Azure Active Directory blade, Company branding is selected. On the right side, the Get a free Premium trial link is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image125.png "Azure Active Directory blade")

    If you already have a Premium Azure Active Directory, skip to Task 2.

5. On the **Activate** blade, select the **Free Trial** link within the **Azure AD Premium P2**, then select **Activate**.

    ![The Free trial link is selected on the Activate blade in the Azure AD Premium P2 box, and the Activate button is highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image126.png "Activate blade")

6. Close the **Azure Active Directory** blades.

-->
## 演習 2: ID とセキュリティ<a name="演習-2:-ID-とセキュリティ"></a>

時間: 75 分

Contoso のコール センター管理アプリケーションは、Contoso の Active Directory 環境からのみアクセスできるようにします。新規 Azure AD テナントを作成し、アプリケーションではそのテナントからのログオンのみを許可し、安全性を確保します。

### タスク 1: Azure AD Premium 試用版を有効化する<a name="タスク-1:-Azure-AD-Premium-試用版を有効化する"></a>

>**注**: このタスクは**オプション**であり、自身のサブスクリプションに関連付けられた Azure AD テナントのグローバル管理者のみが実施できます。

1. 新規のタブまたはインスタンスで Azure 管理ポータル (<http://portal.azure.com>) にアクセスします。

2. 左側のナビゲーション メニューで [**Azure Active Directory**] を選択します。

    ![[Azure Active Directory] メニュー オプション](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Portal")

3. [**Azure Active Directory**] ブレードで [**会社のブランド**] オプションを選択します。

    ![[Azure Active Directory] ブレードで [会社のブランド] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image124.png "[Azure Active Directory] ブレード")

4. 右側のウィンドウで [**無料の Premium 評価版を入手...**] リンクをクリックします。

    ![[Azure Active Directory] ブレード左側で [会社のブランド] が選択されている。右側では [無料の Premium 評価版を入手...] リンクが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image125.png "[Azure Active Directory] ブレード")

    既に Azure Active Directory Premium をご利用の場合は、この手順を省いてタスク 2 に進みます。

5. [**アクティブ化**] ブレードで [**Azure AD Premium P2**] の [**無料試用版**] リンクを選択し、[**アクティブ化**] をクリックします。

    ![[Activate] ブレードで [Azure AD Premium P2] ボックスの [無料試用版] リンクが選択され、[アクティブ化] ボタンが強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image126.png "[アクティブ化] ブレード")

6. [**Azure Active Directory**] ブレードを閉じます。

<!--
### Task 2: Create a new Contoso user

>**Note**: This task is **optional**, and it is valid only if you are a global administrator on the Azure AD tenant associated with your subscription.

1. Navigate to the Azure Management portal, [http://portal.azure.com](http://portal.azure.com/), using a new tab or instance.

2. Select **Azure Active Directory** in the navigation menu to the left.

    ![Screenshot of Azure Active Directory menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Portal")

3. On the **Azure Active Directory** blade, select **Custom Domain names**.

    ![Custom Domain Names menu option screenshot.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image128.png "Custom Domain names")

4. Copy the **Domain Name** for your Azure AD Tenant. It will be in the format: *[your tenant\].onmicrosoft.com*.
    This will be used for creating the new user's Username.

    ![Under Name, the Domain Name is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image129.png "Domain name")

5. On the **Azure Active Directory** blade, select **Users**.

    ![Under Manage, All users is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image130.png "Azure Active Directory blade")

6. Select **+ New user** to add a new user.

    ![The + New User button is boxed in red on the Azure Active Directory blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image131.png "Azure Active Directory blade")

7. On the **User** blade, specify a user's **Name** and **User name**. Specify the **User name** to be at the domain name for your Azure AD Tenant. For example: *tbaker@\[your tenant\].onmicrosoft.com*.

    ![On the User blade, the two previously defined fields (Name and User name) are circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image132.png "User blade")

8. Select the **Show Password** checkbox, and make a note of the password for use later.

    ![The Show Password checkbox is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image133.png "Password section")

9. Select **Create**.

    ![Screenshot of the Create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image134.png "Create button")

-->
### タスク 2: Contoso ユーザーを新規作成する<a name="タスク-2:-Contoso-ユーザーを新規作成する"></a>

>**注**: このタスクは**オプション**であり、自身のサブスクリプションに関連付けられた Azure AD テナントのグローバル管理者のみが実施できます。

1. 新規のタブまたはインスタンスで Azure 管理ポータル (<http://portal.azure.com>) にアクセスします。

2. 左側のナビゲーション メニューで [**Azure Active Directory**] を選択します。

    ![[Azure Active Directory] メニュー オプションのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Portal")

3. [**Azure Active Directory**] ブレードで [**カスタム ドメイン名**] をクリックします。

    ![[カスタム ドメイン名] メニュー オプションのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image128.png "カスタム ドメイン名")

4. 使用する Azure AD テナントの**ドメイン名**をコピーします。ドメイン名の書式は *[テナント名\].onmicrosoft.com* となります。
    これは新規ユーザーのユーザー名を作成するときに使用されます。

    ![[名前] の下でドメイン名が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image129.png "ドメイン名")

5. [**Azure Active Directory**] ブレードで [**ユーザー**] をクリックします。

    ![[管理] の下で [ユーザー] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image130.png "[Azure Active Directory] ブレード")

6. [**+ 新しいユーザー**] を選択して新規ユーザーを追加します。

    ![[Azure Active Directory] ブレードで [+ 新しいユーザー] ボタンが赤で囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image131.png "[Azure Active Directory] ブレード")

7. [**ユーザー**] ブレードでユーザーの**氏名**と**ユーザー名**を指定します。[**ユーザー名**] フィールドでは、Azure AD テナントで使用するドメイン名を指定します。例: *tbaker@\[your tenant\].onmicrosoft.com*.

    ![[ユーザー] ブレードで、前の手順で定義した 2 つのフィールド ([氏名] と [ユーザー名]) が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image132.png "[ユーザー] ブレード")

8. [**パスワードを表示**] チェックボックスをオンにして、後で使用するためにパスワードをメモしておきます。

    ![[パスワードを表示] チェックボックスがオンになっている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image133.png "[パスワード] セクション")

9. [**作成**] をクリックします。

    ![[作成] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image134.png "[作成] ボタン")

<!--
### Task 3: Configure access control for the call center administration Web Application

>**Note**: This task is **optional**, and it is valid only if you have the right to create applications in your Azure AD Tenant.

#### Subtask 1: Enable Azure AD Authentication

1. On the left navigation of the Azure Portal, select **App Services**.

    ![Screenshot of the App Services button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image135.png "App Services button")

2. On the **App Services** blade, select the **Call Center Administration Web app**.

    ![In the App Services blade, under Name, contososportscallcentercp is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image136.png "App Services blade")

3. Select the **Authentication / Authorization** tile.

    ![On the App Service blade, under Settings, Authentication / Authorization is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image137.png "App Service blade")

4. Change **App Service Authentication** to **On**, and change the dropdown to **Log in with Azure Active Directory**.

    ![The Authentication / Authorization section displays with App Service Authentication button set to On, and Log in with Azure Active Directory selected in the Action to take when request is not authenticated drop-down list box.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image138.png "Authentication / Authorization section")

5. Select the **Azure Active Directory**.

    ![In the Authentication Providers section, Azure Active Directory (Not Configured) is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image139.png "Authentication Providers section")

6. On the **Azure Active Directory Settings** blade, change **Management mode** to **Express**.

    ![At the bottom of the Azure Active Directory Settings blade, Management mode is set to Express.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image140.png "Azure Active Directory Settings blade")

7. Select **OK**.

    ![Screenshot of the OK button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image141.png "OK button")

8. Change the **Action to take when request is not authenticated** option to **Login with Azure Active Directory**.

    ![The Action to take when request is not authenticated field is set to Log in with Azure Authentication.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image142.png "Action to take field")

9. In the **Authentication / Authorization** blade, select **Save**.

    ![The Save button is circled in the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image143.png "App Service blade")

#### Subtask 2: Verify the call center administration website uses the access control logon

1. Close your browser (or use an alternative), and launch a browser is **InPrivate or Incognito mode**. Navigate to the **Call Center Administration** website.

2. The browser will redirect to the non-branded Access Control logon URL. You can log on with your Microsoft account or the **Contoso test user** you created earlier.

    ![Microsoft login prompt.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image144.png "Microsoft login prompt")

3. After you log on and **accept the consent**, your browser will be redirected to the Contoso Sports League Admin webpage.

    ![The Contoso Sports League Admin webpage displays with one Completed Order.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image145.png "Contoso Sports League Admin webpage")

4. Verify in the upper-right corner you see the link **Logged In**. If it is not configured, you will see **Sign in**.

    ![Screenshot of the Logged In message.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image146.png "Logged in message") ![Screenshot of the Sign In link.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image147.png "Sign in link")

-->
### タスク 3: コール センター管理 Web アプリケーションのアクセス制御を構成する<a name="タスク-3:-コール-センター管理-Web-アプリケーションのアクセス制御を構成する"></a>

>**注**: このタスクは**オプション**であり、使用する Azure AD テナントでアプリケーション作成権限を所有している場合にのみこのタスクを実施できます。

#### サブタスク 1: Azure AD 認証を有効化する<a name="サブタスク-1:-Azure-AD-認証を有効化する"></a>


1. Azure Portal の左側のナビゲーション ウィンドウで [**App Service**] を選択します。

    ![[App Service] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image135.png "[App Service] ボタン")

2. [**App Service**] ブレードで**コール センター管理 Web アプリ**を選択します。

    ![[App Service] ブレードの [名前] で contososportscallcentercp が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image136.png "[App Service] ブレード")

3. [**認証/承認**] タイルを選択します。

    ![[App Service] ブレードの [設定] で [認証/承認] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image137.png "[App Service] ブレード")

4. [**App Service 認証**] を [**オン**] に変更し、ドロップダウン メニューで [**Azure Active Directory でのログイン**] を選択します。

    ![[認証/承認] セクションに表示されている [App Service 認証] ボタンが [オン] に設定され、[要求が認証されない場合に実行するアクション] ドロップダウン メニューで [Azure Active Directory でのログイン] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image138.png "[認証/承認] セクション")

5. [**Azure Active Directory**] を選択します。

    ![[認証プロバイダー] セクションで [Azure Active Directory (未構成)] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image139.png "[認証プロバイダー] セクション")

6. [**Azure Active Directory の設定**] ブレードで [**管理モード**] を [**簡易**] に変更します。

    ![[Azure Active Directory の設定] ブレード下部の [管理モード] が [簡易] に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image140.png "[Azure Active Directory の設定] ブレード")

7. [**OK**] を選択します。

    ![[OK] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image141.png "[OK] ボタン")

8. [**要求が認証されない場合に実行するアクション**] オプションを [**Azure Active Directory でのログイン**] に変更します。

    ![[要求が認証されない場合に実行するアクション] フィールドが [Azure Active Directory でのログイン] に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image142.png "[実行するアクション] フィールド")

9. [**認証/承認**] ブレードで [**保存**] をクリックします。

    ![[App Service] ブレードの [保存] ボタンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image143.png "[App Service] ブレード")

#### サブタスク 2: コール センター管理 Web サイトへのログオンにアクセス制御が適用されていることを検証する<a name="サブタスク-2:-コール-センター管理-Web-サイトへのログオンにアクセス制御が適用されていることを検証する"></a>

1. いったんブラウザーを閉じてから (または他のブラウザーを) **InPrivate またはシークレット モード**で開きます。**コール センター管理** Web サイトにアクセスします。

2. ブラウザーはブランドが設定されていないアクセス制御ログオン URL にリダイレクトされます。Microsoft アカウント、または前の手順で作成した **Contoso テスト ユーザー**でログオンできます。

    ![マイクロソフトのログイン プロンプト](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image144.png "マイクロソフトのログイン プロンプト")

3. ログオンして**同意書を承認する**と、ブラウザーが Contoso Sports League 管理 Web ページにリダイレクトされます。

    ![Contoso Sports League 管理 Web ページで 1 商品の注文完了が示されている画面](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image145.png "Contoso Sports League 管理 Web ページ")

4. 右上隅に [**ログイン中**] リンクが表示されていることを確認します。構成されていない場合は [**サインイン**] リンクが表示されます。

    ![[ログイン中] メッセージのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image146.png "[ログイン中] メッセージ") ![[サインイン] リンクのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image147.png "[サインイン] リンク")

<!--
### Task 4: Apply custom branding for the Azure Active Directory logon page

>**Note**: this task is **optional**, and it is valid only if you are a global administrator on the Azure AD tenant associated with your subscription, and you completed the Enabling Azure AD Premium exercise.

1. Navigate to the Azure Management portal, [http://portal.azure.com](http://portal.azure.com/), using a new tab or instance.

2. In the navigation menu to the left, select **Azure Active Directory**.

    ![The Azure Active Directory menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Active Directory")

3. On the **Azure Active Directory** blade, select **Company branding**.

    ![On the Azure Active Directory blade, Company branding is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image148.png "Azure Active Directory blade")

4. Select the **Configure...** information box.

    ![The Configure company branding link is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image149.png "Configure company branding link")

5. On the **Configure company branding** blade, select the `default_signin_illustration.jpg` image file from `C:\MCW` for the **Sign-in page image**.

    ![The Configure company branding blade displays the default sign in picture of the Contoso sports league text, and a person on a bicycle. Below that, the Select a file field and browse icon is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image150.png "Configure company branding blade")

6. Select the `logo-60-280.png` image file from the supplementary files for the **Banner image**.

    ![The Contoso sports league banner text displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image151.png "Contoso sports league banner")

7. Select **Save**.

    ![The Save button is circled on the Configure company branding blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image152.png "Configure company branding blade")

-->
### タスク 4: Azure Active Directory のログオン ページにカスタム ブランディングを適用する<a name="タスク-4:-Azure-Active-Directory-のログオン-ページにカスタム-ブランディングを適用する"></a>

>**注**: このタスクは**オプション**です。自身のサブスクリプションに関連付けられた Azure AD テナントのグローバル管理者であり、「Azure AD Premium 試用版を有効化する」の課題を完了している場合のみこのタスクを実施できます。

1. 新規のタブまたはインスタンスで Azure 管理ポータル (<http://portal.azure.com>) にアクセスします。

2. 左側のナビゲーション メニューで [**Azure Active Directory**] を選択します。

    ![[Azure Active Directory] メニュー オプション](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image123.png "Azure Active Directory")

3. [**Azure Active Directory**] ブレードで [**会社のブランド**] を選択します。

    ![[Azure Active Directory] ブレードで [会社のブランド] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image148.png "[Azure Active Directory] ブレード")

4. [**構成...**] 情報ボックスを選択します。

    ![[会社のブランドを構成する] リンクが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image149.png "[会社のブランドを構成する] リンク")

5. [**会社のブランドを構成する**] ブレードで、**サインイン ページの画像**として `C:\MCW` フォルダー内の `default_signin_illustration.jpg` という画像を選択します。

    ![[会社のブランドを構成する] ブレードに Contoso sports league という文字と自転車に乗っている人の写真があしらわれた既定のサインイン画像が表示されている。その下の [ファイルを選択] フィールドと参照アイコンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image150.png "[会社のブランドを構成する] ブレード")

6. 提供されたファイルの中から `logo-60-280.png` を**バナー画像**として選択します。

    ![Contoso sports league というバナー テキストが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image151.png "Contoso sports league のバナー")

7. [**保存**] をクリックします。

    ![[会社のブランドを構成する] ブレードで [保存] ボタンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image152.png "[会社のブランドを構成する] ブレード")

<!--
### Task 5: Verify the branding has been successfully applied to the Azure Active Directory logon page

1. Close any previously authenticated browser sessions to the call center administration website, reopen using InPrivate or Incognito mode, and navigate to the **call center administration** website.

2. The browser will redirect to the branded access control logon URL.

    ![The Call center administration Sign in webpage displays in an InPrivate / Incognito browser.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image153.png "Call center administration website")

3. After you log on, your browser will be redirected to the Contoso Sports League Admin webpage.

    ![The Contoso Sports League Admin webpage displays with one completed order.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image145.png "Contoso Sports League Admin webpage")

4. Verify in the upper-right corner you see the link **Logged in**.

    ![Screenshot of the Logged in message.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image146.png "Logged in message")

    >**Note**: If you run the app using localhost, ensure connection strings within all the appsettings.json files in the solution have the placeholders removed with actual values. Search on appsettings.json in the Visual Studio Solution Explorer to come up with the list.

-->
### タスク 5: Azure Active Directory のログオン ページにブランディングが正常に適用されていることを検証する<a name="タスク-5:-Azure-Active-Directory-のログオン-ページにブランディングが正常に適用されていることを検証する"></a>

1. これまでに開いた、コール センター管理 Web サイトの認証を受けたブラウザー セッションをすべて閉じ、InPrivate またはシークレット モードで再起動して、**コール センター管理** Web サイトにアクセスします。

2. ブラウザーはブランドが適用されたアクセス制御ログオン URL にリダイレクトされます。

    ![InPrivate またはシークレット モードのブラウザーで表示されたコール センター管理 Web サイトのサインイン ページ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image153.png "コール センター管理 Web サイト")

3. ログオンすると、ブラウザーが Contoso Sports League 管理 Web ページにリダイレクトされます。

    ![Contoso Sports League 管理 Web ページで 1 商品の注文完了が示されている画面](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image145.png "Contoso Sports League 管理 Web ページ")

4. 右上隅に [**ログイン中**] リンクが表示されていることを確認します。

    ![[ログイン中] メッセージのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image146.png "[ログイン中] メッセージ")

    >**注**: ローカル ホストでアプリを実行する場合、ソリューションのすべての appsettings.json ファイルに含まれる接続文字列のプレースホルダーが実際の値に変更されていることを確認します。Visual Studio ソリューション エクスプローラーで appsettings.json を検索して、リストを確認します。

<!--
## Exercise 3: Enable Azure B2C for customer site

Duration: 75 minutes

In this exercise, you will configure an Azure AD Business to Consumer (B2C) instance to enable authentication and policies for sign-in, sign-out and profile policies for the Contoso E-Commerce site.

### Task 1: Create a new directory

1. Log in to the Azure portal by using your existing Azure subscription or by starting a free trial. In the left-hand navigation menu, select **+Create a resource**. Then, search for and select **Azure Active Directory B2C** and select **Create** on the new blade that pops up.

    ![In the Everything blade, the active directory B2C text is in the Search field, and under Results, Azure Active Directory B2C displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image156.png "Everything blade")

2. In the new blade, select **Create a new Azure AD B2C Tenant**. Then, enter the name as **ContosoB2C** and a unique domain name and region. Then, select **Create**. After directory creation completes, select the link in the new information tile that reads **Click here to manage your new directory**.

    ![In the Azure Portal, under Create new B2C Tenant or Link to existing Tenant, Create a new Azure AD B2C Tenant is selected. On the right, the word \"here,\" which is a link, is circled in the Select here to manage your new directory message.](media/2019-03-28-09-29-30.png "Azure Portal")

    ![In the Azure Portal, under Create new B2C Tenant or Link to existing Tenant, Create a new Azure AD B2C Tenant is selected. On the right, the word \"here,\" which is a link, is circled in the Select here to manage your new directory message.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image157.png "Azure Portal")

3. Select the orange **No Subscription** message for instructions on how to link to an active subscription.

    ![In the Azure Portal, on the left, the \"No subscription linked to this B2C tenant or the Subscription needs your attention\" message is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image158.png "Azure Portal")

    ![The three steps to link the B2C tenant to an Azure subscription are circled.](media/2019-08-25-17-45-26.png "Azure Portal")

    >**Note**: Essentially, you will need to switch back to your previous Azure AD tenant, and then launch the Azure AD B2C creation wizard again.

4. Select **Link an existing Azure AD B2C Tenant to my Azure subscription,** and select the Tenant you just created in the dropdown list and the existing resource group **contososports**. Then, select **Create**.

    ![In the Create new B2C Tenant or Link to existing Tenant blade, on the left, Link an existing Azure AD B2C Tenant to my Azure subscription is selected. On the right, in the Azure AD B2C Resource blade, the Azure AD B2C Tenant drop-down field is contosodb2ccustsitecp.onmicrosoft.com. The Resource group is using the existing contososports.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image159.png "Create new B2C Tenant or Link to existing Tenant")

5. After creation completes, open the new Azure AD B2C tenant by selecting **Resource Groups** in the navigation menu to the left and, then, **contososports**. Then, in the new blade, select the B2C tenant you just created.

    ![In the contososports resource group, the new B2C tenant is boxed in red.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/b2ctenant_in_rg.png "Azure AD B2C Settings window")

6. In the new blade, select the **B2C Settings** tile for the new B2C tenant. You will be taken to the new subscription for this tenant.

    ![In the Azure AD B2C tenant window, on the left, All Settings is selected. In the bottom right section, the Azure AD B2C Settings tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image160.png "Azure AD B2C Settings window")

7. In the new tab that opened, under the **MANAGE** menu area of the open **Azure AD B2C** blade, select **Applications**. Then, in the new pane, select **+Add**.

    ![In the Azure AD B2C Settings window, on the left, All Settings is selected. In the middle, under Settings, under Manage, Applications is selected. On the right, the Add button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/b2c-add-app-link.png "Azure AD B2C Settings window")

### Task 2: Add a new application

1. Specify the following configuration options for the Web App:

   - Name: **Contoso B2C Application**

   - Include Web App / web API: **Yes**

   - Allow Implicit Flow: **Yes**

   - Reply URL: `https://[your web url].azurewebsites.net/signin-oidc-b2c` _(This should be the HTTPS URL to the Contoso E-Commerce Site.)_

   ![The New application fields are set to the previously defined values.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image161.png "New application")

2. Select **Create**.

3. Back on the **Azure AD B2C** blade in the **Applications** screen, copy the application ID of your new application to Notepad to use later. Keep this tab open for the next task.

     ![B2C application name and ID values are shown.](media/2019-04-11-08-36-28.png "Azure AD B2C screen")

### Task 3: Create Policies, Sign up and sign in

1. Navigate back to the **Azure AD B2C** blade that was opened in the last task.

2. To enable sign-up on your application, you will need to create a sign-up policy. This policy describes the experiences consumers will go through during sign-up and the contents of tokens the application will receive on successful sign-ups. Select **User flows** link on the left menu and then **+New user flow** link at the top of the blade.

    ![In the Azure Portal, on the left, Azure AD B2C - User Flows selected.](media/2019-03-28-12-17-22.png "Azure AD B2C - User Flows selected")

3. Select the **Sign up and sign in** link.
  
    ![Recommended for most applications results is displayed. Sign up and sign in link is highlighted.](media/2019-03-28-12-20-42.png "Sign up and sign in link")

4. Enter **SignUp** in the **Name** field.

    ![The unique Azure AD B2C user flow name is displayed.](media/2019-04-11-08-40-58.png "User Flow Name")

5. Select **Identity providers**, and select **Email Signup**. Optionally, you can also select social identity providers (if previously configured for the tenant). Select **OK**.

    ![In the Add policy blade, Identity providers is selected. In the Select identity providers blade, Email signup is selected.](media/2019-03-28-12-25-35.png "Add policy and Select identity providers blades")

6. **Multifactor authentication** set to **Disabled**.

7. **User attributes and claims**.
    - Select the **Show more...** link.

    ![In the Azure AD B2C - User flow policy - create user flow pane, the Show more link is highlighted after the default user attributes and claims.](media/2019-03-28-12-38-39.png "Show more link")

8. Select the following **Collect attributes**:

    - **Country/Region**
    - **Display Name**
    - **Postal Code**

9. Select the following **Return claims**:

    - **Display Name**
    - **Identity Provider**
    - **Postal Code**
    - **User is new**
    - **User's Object ID**
  
10. Review your selections, select **OK**.

    ![Azure AD B2C - User flow - Review the collection and return claims columns.](media/2019-03-28-12-44-04.png "Collection and return claims")

11. Select **Create**. Observe the policy just created appears as **B2C\_1\_SignUp** (the **B2C\_1\_** fragment is automatically added) in the **Sign-up policies** blade.

    >**Note**: The page may take a few minutes to load/refresh after you start creating the policy.

    ![Azure AD B2C - User flows list.  Shows the newly created flow.](media/2019-03-28-12-46-48.png "Azure AD B2C User Flow List")

12. Open the policy by selecting the link in the list e.g. **B2C\_1\_SignUp**.

13. Select **Run user flow** and open the dialog.

    ![In the Policies section, Sign-in policies is selected.](media/2019-03-28-12-52-27.png "Policies section")

14. Select **Run user flow** - Choose application and run user flow. 

    ![Choose application options are displayed. Contoso B2C Application option is selected. Run user flow button is displayed.](media/2019-03-28-12-55-51.png "Test the user flow")

15. A browser tab/window will open that looks like the following screenshot.

    ![Test the user flow.  Sample sign in presented in the browser.](media/2019-03-28-13-00-01.png "Test the user flow")
    
16. Select **Sign up now**.

    ![Sign up now fields are presented to the user.](media/2019-03-28-13-02-25.png "Sign up now")

### Task 4: Create a profile editing policy

To enable profile editing on your application, you will need to create a profile editing policy. This policy describes the experiences that consumers will go through during profile editing and the contents of tokens that the application will receive on successful completion.

1. Select **User flows** link on the left blade.

2. Select **+ New user flow** link at the top of the blade.

3. Select the **All** tab link.

    ![The Create a user flow pane is displayed.  The ALL tab is selected. All user flows are displayed. The Profile editing has an arrow pointing at it.](media/2019-03-28-16-19-55.png "Select Profile Editing")

3. Select **Profile editing**.

4. The Name determines the profile editing policy name used by your application. For example, enter **EditProfile**.

    ![In the Add policy blade, Identity providers (1 Selected) is selected. Identities providers - select Local Account SignIn.](media/2019-03-28-16-24-26.png "select Local Account SignIn")

5. Select Identity providers, and then "**Local Account SignIn**."

6. Select the **Show more...** link.

7. Select **Collect attributes**. Here, you choose attributes the consumer can view and edit.

    For now, select the following:

    - **Country/Region**
    - **Display Name**
    - **Job Title**
    - **Postal Code**
    - **State/Province**
    - **Street Address**

8. Select **Return claims**. Here, you choose claims you want returned in the tokens sent back to your application after a successful profile editing experience.

    For now, select the following:

    - **Display Name**
    - **Postal Code**

    ![Sign up - User attributes selected blade.](media/2019-03-28-16-28-53.png "Sign up - User attributes selected blade")

9. Select **OK**.

10. Select **Create**. Observe the policy just created appears as \"**B2C\_1\_EditProfile**\" (the **B2C\_1\_** fragment is automatically added) in the **Profile editing policies** blade.

11. Open the policy by selecting **B2C\_1\_EditProfile**, then **Run user flow**.

12. Select **Contoso B2C application** in the **Select Application** drop-down.

13. Select **Run user flow**. A new browser tab opens, and you can run through the profile editing consumer experience in your application.

### Task 5: Create a password reset policy

To enable profile editing on your application, you will need to create a profile password reset. This policy describes the experiences that consumers will go through during password reset and the contents of tokens that the application will receive on successful completion.

1. Select **User flows** link on the left blade.

2. Select **+ New user flow** link at the top of the blade.

3. Select **Password reset**.

    ![The Create a user flow pane is displayed.  The Recommended tab is selected. The Password reset is highlighted.](media/2020-03-19-09-47-15.png "Select Password reset")

4. The Name determines the profile editing policy name used by your application. For example, enter **SSPR**.

    ![In the Add policy blade, Identity providers (1 Selected) is selected. Identities providers - select Reset password using email address.](media/2020-03-19-09-50-24.png "select Reset password using email address")

5. Select Identity providers, and then "**Reset password using email address**."

6. Select the **Show more...** link.

7. Select **Return claim**. Here, you choose attributes about the user that are returned to the application in the token.

    For now, select the following:

    - **Email Addresses**
    - **Given Name**

    ![Return claim attributes selected blade.](media/2020-03-19-09-54-28.png "Return claims")

8. Select **OK**.

10. Select **Create**. Observe the policy just created appears as \"**B2C\_1\_SSPR**\" (the **B2C\_1\_** fragment is automatically added) in the **Profile editing policies** blade.

11. Open the policy by selecting **B2C\_1\_SSPR**, then **Run user flow**.

12. Select **Contoso B2C application** in the **Select Application** drop-down.

13. Select **Run user flow**. A new browser tab opens, and you can run through the profile editing consumer experience in your application.

### Task 6: Modify the Contoso.App.SportsLeague.Web

1. Expand the **Contoso.Apps.SportsLeague.Web** project. Find the **Startup.cs** code file, locate the `public void ConfigureServices(` method declaration, then add the following line of code to the bottom of this method:

    ```csharp
    services.AddAuthentication(Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults.AuthenticationScheme)
                .AddAzureADB2C(options => Configuration.Bind("AzureADB2C", options));
    ```

    ![The Startup.cs file with the "app.UseAuthorization();" line of code highlighted.](media/2019-04-19-15-08-40.png "Startup.cs")

2. Add the following `using` directives to the top of the **Startup.cs** code file:

    ```
    using Microsoft.AspNetCore.Authentication;
    using Microsoft.AspNetCore.Authentication.AzureADB2C.UI;
    ```

3. Locate the `app.UseAuthentication();` line within the `public void Configure` method, and add the following line of code after it:

    ```
    app.UseAuthentication();
    app.UseAuthorization();
    ```

    The result will look similar to the following:

    ![app.UseAuthentication code inserted.](media/2020-03-18-14-44-13.png "app.UseAuthentication code inserted")

4. Locate the Azure AD B2C name by navigating to your resource group. Copy the name to Notepad.

    ![List of all of the resources within the ContosoSports resource group. Pointing to the B2C tenant name.](media/2019-03-28-16-51-14.png "Locate B2C tenant name")

5. Next, using the Azure Management Portal, using your main subscription, open the Contoso Web App blade, and select **Configuration**.

6. Add the following settings in the **Application Settings** section:

   - AzureADB2C:Instance - `https://[your Azure AD B2C name].b2clogin.com/tfp/`
   - AzureADB2C:ClientId - **B2C Application ID you copied down earlier**.
   - AzureADB2C:CallbackPath - `/signin-oidc-b2c`
   - AzureADB2C:Domain - **[your Azure AD B2C name].onmicrosoft.com**
   - AzureADB2C:SignUpSignInPolicyId - `B2C_1_SignUp`
   - AzureADB2C:ResetPasswordPolicyId - `B2C_1_SSPR`
   - AzureADB2C:EditProfilePolicyId - `B2C_1_EditProfile`

7. Select **Save**.

### Task 7: Send authentication requests to Azure AD

Your app is now properly configured to communicate with Azure AD B2C by using ASP.NET Core Identity. OWIN has taken care of all of the details of crafting authentication messages, validating tokens from Azure AD, and maintaining user session. All that remains is to initiate each user's flow.

1. Right select the **Controllers** folder, and select **Add** -\> **Controller**.

    ![In Solution Explorer, in the right-click menu for the Controllers folder, Add is selected, and from its menu, Controller is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image177.png "Solution Explorer")

2. Select **MVC Controller -- Empty** and then select **Add**. Replace **DefaultController** value with **AccountController** in the **Add Controller** dialog box.

    ![On the left of the Add Scaffold window, Installed / Controller is selected. In the center of the window, MVC 5 Controller - Empty is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image178.png "Add Scaffold window")

3. Add the following using statement to the top of the controller:

    ```csharp
    using Microsoft.AspNetCore.Authentication;
    using Microsoft.AspNetCore.Authentication.AzureADB2C.UI;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    ```

4. Locate the default controller **Index** method.

    ![The Default controller method Index is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image179.png "Default controller method Index")

    Replace the method with the following code, then **Save** the file:

    ```csharp
    // Controllers\AccountController.cs

    private string _editProfilePolicyId;

    public AccountController(IConfiguration configuration)
    {
        _editProfilePolicyId = configuration.GetValue<string>("AzureADB2C:EditProfilePolicyId");
    }

    public ActionResult SignIn()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return Challenge(new AuthenticationProperties() { RedirectUri = "/" }, AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }
            
    public ActionResult SignUp()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return Challenge(new AuthenticationProperties() { RedirectUri = "/" }, AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }

    public ActionResult Profile()
    {
        if (User.Identity.IsAuthenticated)
        {
                var properties = new AuthenticationProperties() { RedirectUri = "/" };
                properties.Items[AzureADB2CDefaults.PolicyKey] = _editProfilePolicyId;
                return Challenge(
                    properties,
                    AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }

    public ActionResult SignOut()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return RedirectToAction("Index", "Home");
        }
        string redirectUri = Url.Action("Index", "Home", null, Request.Scheme);
        var properties = new AuthenticationProperties
        {
            RedirectUri = redirectUri
        };
        return SignOut(properties, AzureADB2CDefaults.CookieScheme, AzureADB2CDefaults.OpenIdScheme);
    }
    ```

5. Save the file.

### Task 8: Display user information

When you authenticate users by using OpenID Connect, Azure AD returns an ID token to the app that contains **claims**. These are assertions about the user. You can use claims to personalize your app. You can access user claims in your controllers via the ClaimsPrincipal.Current security principal object.

1. Open the **Controllers\\HomeController.cs** file and add the following using statements at the end of the other using statements at the top of the file:

    ```csharp
    using Contoso.Apps.SportsLeague.Web.Models;
    using Microsoft.AspNetCore.Authorization;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    ```

2. Still in the **Controllers\\HomeController.cs** file, add the following method to the **HomeController** class:

    ```csharp
    [Authorize]
    public ActionResult Claims()
    {
        var displayName = User.Identity.Name;
        ViewBag.DisplayName = displayName;
        ViewBag.Claims = User.Claims;
        return View();
    }
    ```

3. You can access any claim that your application receives in the same way. A list of all the claims the app receives is available for you on the **Claims** page. In Visual Studio on the Contoso.Apps.SportsLeague.Web object, right-click on **Views -\> Home,** select **Add -\> View** and name it **Claims.**  Select **OK**.

    ![In Solution Explorer, on the right-click menu for Views\\Home, Add is selected, and from its menu, View is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180.png "Solution Explorer")

4. Open the **Claims.cshtml** file and replace the code with the following:

    ```csharp
    @using System.Security.Claims
    @{
        ViewBag.Title = "Claims";
    }
    <h2>@ViewBag.Title</h2>

    <h4>Claims Present in the Claims Identity: @ViewBag.DisplayName</h4>

    <table class="table-hover claim-table">
        <tr>
            <th class="claim-type claim-data claim-head">Claim Type</th>
            <th class="claim-data claim-head">Claim Value</th>
        </tr>

        @foreach (Claim claim in ViewBag.Claims)
        {
            <tr>
                <td class="claim-type claim-data">@claim.Type</td>
                <td class="claim-data">@claim.Value</td>
            </tr>
        }
    </table>
    ```

5. Right-click on the **Views -\> Shared** folder, select **Add**, add a new **View**, and set it to **Create as a partial view**. Specify **\_LoginPartial** for the name.

    ![In Solution Explorer, on the right-click menu for Views\\Shared, Add is selected, and from its menu, View is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180.png  "Solution Explorer")

    !["Create as a partial view" is highlighted.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180-b.png "Add MVC View")

6. Add the following code to the razor partial view to provide a sign-in and sign-out link as well as a link to edit the user's profile:

    ```html
    @if (User.Identity.IsAuthenticated)
    {
        <text>
            <ul class="nav navbar-nav navbar-right">
                <li>
                    <a id="profile-link">@User.Identity.Name</a>
                    <div id="profile-options" class="nav navbar-nav navbar-right">
                        <ul class="profile-links">
                            <li class="profile-link">
                                @Html.ActionLink("Edit Profile", "Profile", "Account")
                            </li>
                        </ul>
                    </div>
                </li>
                <li>
                    @Html.ActionLink("Sign out", "SignOut", "Account")
                </li>
            </ul>
        </text>
    }
    else
    {
        <ul class="nav navbar-nav navbar-right">
            <li>@Html.ActionLink("Sign up", "SignUp", "Account", routeValues: null, htmlAttributes: new { id = "signUpLink" })</li>
            <li>@Html.ActionLink("Sign in", "SignIn", "Account", routeValues: null, htmlAttributes: new { id = "loginLink" })</li>
        </ul>
    }
    ```

7. Open **Views\\Shared\\\_Layout.cshtml** in Visual Studio. Locate the header-top div, and add the line that starts with **@Html.ActionLink** and the line that starts with **@Html.Partial**.

    ```html
    <div class="header-top">
        <div class="container">
            <div class="row">
                <div class="header-top-left">
                <a href="#"><i class="fa fa-twitter"></i></a>
                <a href="#"><i class="fa fa-facebook"></i></a>
                <a href="#"><i class="fa fa-linkedin"></i></a>
                <a href="#"><i class="fa fa-instagram"></i></a>
                </div>
                <div class="header-top-right">
                    <a href="#" class="top-wrap"><span class="icon-phone">Call today: </span> (555) 555-8000</a>
                    @Html.ActionLink("Claims", "Claims", "Home")
                </div>
                @Html.Partial("_LoginPartial")
            </div>
        </div>
    </div>
    ```

### Task 9: Run the sample app

1. Right-click on the **Contoso.Apps.SportsLeague.Web** project, and select **Publish**. Follow the steps to deploy the updated application to the Microsoft Azure Web App.

    Launch a browser outside of Visual Studio for testing if the page loads in Visual Studio.

2. Test out Sign up.

3. Next, test Sign out.

4. When you select Claims and are not signed in, it will bring you to the sign-in page and then display the claim information. Sign in, and test Edit Profile.

    ![On the Contoso website, the following links are circled: Claims, Sign up, and Sign in.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image182.png "Contoso website")

    Claims information page:    
    ![On the Contoso website, the following links are circled: Russell, Sign out, and Edit Profile.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image183.png "Contoso website, Claims information page")

-->
## 演習 3: 顧客サイト用 Azure B2C を有効化する<a name="演習-3:-顧客サイト用-Azure-B2C-を有効化する"></a>

時間: 75 分

この演習では、Azure AD Business to Consumer (B2C) インスタンスを構成し、Contoso の eコマース サイトの認証、サインインおよびサインアウトのポリシー、プロファイル ポリシーを有効化します。

### タスク 1: ディレクトリを新規作成する<a name="タスク-1:-ディレクトリを新規作成する"></a>

1. 所有している Azure サブスクリプションを使用するか、または無料試用版で Azure Portal にログインします。左側のナビゲーション メニューで [**+リソースの作成**] を選択します。次に **Azure Active Directory B2C** を検索して選択し、ポップアップした新規ブレードで [**作成**] をクリックします。

    ![[すべて] ブレードの [検索] フィールドに「Active Directory B2C」と入力されており、[結果] に Azure Active Directory B2C が表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image156.png "[すべて] ブレード")

2. 新規ブレードで [**新しい Azure AD B2C テナントを作成する**] を選択します。次に、「**ContosoB2C**」という名前と一意のドメイン名を入力し、リージョンを選択します。その後、[**作成**] をクリックします。ディレクトリが作成されたら、[**新規ディレクトリを管理するにはここをクリック**] という新しい情報タイルのリンクを選択します。

    ![Azure Portal の [新しい B2C テナントの作成または既存のテナントへのリンク] で [新しい Azure AD B2C テナントを作成する] が選択されている。右側の「新規ディレクトリを管理するにはここをクリック」というメッセージの中のリンク部分の「ここ」が赤で囲まれている](media/2019-03-28-09-29-30.png "Azure Portal")

    ![Azure Portal の [新しい B2C テナントの作成または既存のテナントへのリンク] で [新しい Azure AD B2C テナントを作成する] が選択されている。右側の「新規ディレクトリを管理するにはここをクリック」というメッセージの中のリンク部分の [\"ここ\"] が赤で囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image157.png "Azure Portal")

3. オレンジ色の「**サブスクリプションがありません**」というメッセージを選択し、有効なサブスクリプションにリンクする方法を確認します。

    ![Azure Portal の左側の「この B2C テナントにリンクされたサブスクリプションがありません。サブスクリプションを確認してください。」というメッセージが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image158.png "Azure Portal")

    ![B2C テナントから Azure サブスクリプションへのリンクを作成する 3 つの手順が囲まれている](media/2019-08-25-17-45-26.png "Azure Portal")

    >**注**: 原則的には、前の Azure AD テナントに戻り、Azure AD B2C 作成ウィザードを再び開始する必要があります。

4. [**既存の Azure AD B2C テナントを Azure サブスクリプションにリンクする**] をクリックし、先ほど作成したテナントをドロップダウン リストから選択し、既存のリソース グループの **contososports** を指定します。その後、[**作成**] をクリックします。

    ![[新しい B2C テナントの作成または既存のテナントへのリンク] ブレードの左側では [既存の Azure AD B2C テナントを Azure サブスクリプションにリンクする] が選択されている。右側の [Azure AD B2C リソース] ブレードの [Azure AD B2C テナント] ドロップダウン リストでは contosodb2ccustsitecp.onmicrosoft.com が選択されている。このリソース グループでは、既存の contososports が使用される](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image159.png "新しい B2C テナントの作成または既存のテナントへのリンク")

5. 作成が完了したら、左側のナビゲーション メニューで [**リソース グループ**]、**contososports** の順に選択して新しい Azure AD B2C テナントを開きます。次に、作成した B2C テナントを新しく開いたブレードで選択します。

    ![contososports リソース グループの新しい B2C テナントが赤で囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/b2ctenant_in_rg.png "[Azure AD B2C の設定] ウィンドウ")

6. 新しく開いたブレードで、新規作成した B2C テナントの [**B2C の設定**] タイルを選択します。このテナントで使用される新しいサブスクリプションに移動します。

    ![[Azure AD B2C テナント] ウィンドウ左側の [すべての設定] が選択されている。右下のセクションでは [Azure AD B2C の設定] タイルが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image160.png "[Azure AD B2C の設定] ウィンドウ")

7. 新しく開いたタブの [**管理**] メニューで、[**Azure AD B2C**] ブレード、[**アプリケーション**] の順に選択します。次に、新しいウィンドウで [**+追加**] をクリックします。

    ![[Azure AD B2C の設定] ウィンドウ左側の [すべての設定] が選択されている。中央の [設定]、[管理] で [アプリケーション] が選択されている。右側のセクションでは [追加] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/b2c-add-app-link.png "[Azure AD B2C の設定] ウィンドウ")

### タスク 2: アプリケーションを新規作成する<a name="タスク-2:-アプリケーションを新規作成する"></a>

1. Web アプリの以下の構成オプションを指定します。

   - 名前: **Contoso B2C Application**

   - Web アプリ/Web API を含める: **はい**

   - 暗黙的フローを許可する: **はい**

   - 応答 URL: `https://[your web url].azurewebsites.net/signin-oidc-b2c` (Contoso の eコマース Web サイトの HTTPS プロトコルの URL を指定)

   ![[新しいアプリケーション] フィールドが先に定義された値に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image161.png "新しいアプリケーション")

2. [**作成**] をクリックします。

3. 後で使用するため、[**アプリケーション**] 画面の [**Azure AD B2C**] ブレードに戻って、新しいアプリケーションのアプリケーション ID をメモ帳にコピーします。このタブは次のタスクでも使用するため、開いたままにしておきます。

     ![B2C アプリケーションの名前と ID の値が表示されている](media/2019-04-11-08-36-28.png "[Azure AD B2C] 画面")

### タスク 3: サインアップとサインインのポリシーを作成する<a name="タスク-3:-サインアップとサインインのポリシーを作成する"></a>

1. 前のタスクで開いた [**Azure AD B2C**] ブレードに戻ります。

2. アプリケーションにサインアップできるようにするためには、サインアップ ポリシーを作成する必要があります。このポリシーは、一般ユーザーがサインアップするときのユーザー エクスペリエンスと、サインアップ完了時にアプリケーションに送られるトークンの内容を示します。左側のメニューの [**ユーザー フロー**] リンクを選択し、ブレード上部の [**+新しいユーザー フロー**] をクリックします。

    ![Azure Portal の左側で [Azure AD B2C]、[ユーザー フロー] の順に選択](media/2019-03-28-12-17-22.png "[Azure AD B2C]、[ユーザー フロー] の順に選択")

3. [**サインアップとサインイン**] リンクを選択します。
  
    ![大多数のアプリケーションに推奨される結果が表示されている。[サインアップとサインイン] リンクが強調表示されている](media/2019-03-28-12-20-42.png "[サインアップとサインイン] リンク")

4. [**名前**] フィールドに「**SignUp**」と入力します。

    ![一意の Azure AD B2C ユーザー フロー名が表示されている](media/2019-04-11-08-40-58.png "ユーザー フロー名")

5. [**ID プロバイダー**]、[**電子メールのサインアップ**] の順に選択します。任意で、ソーシャル ID プロバイダーを選択することもできます (テナントで事前に構成されている場合)。[**OK**] を選択します。

    ![[ポリシーの追加] ブレードで ID プロバイダーが選択されている。[ID プロバイダーの選択] ブレードで [電子メールのサインアップ] が選択されている](media/2019-03-28-12-25-35.png "[ポリシーの追加] の [ID プロバイダーの選択] ブレード")

6. [**多要素認証**] を [**無効**] に設定します。

7. [**ユーザー属性と要求**] で次のように操作します。
    - [**さらに表示する...**] リンクを選択します。

    ![[Azure AD B2C - ユーザー フロー (ポリシー)] の [ユーザー フローを作成する] ウィンドウで、既定のユーザー属性と要求の後に [さらに表示する] リンクが強調表示されている](media/2019-03-28-12-38-39.png "[さらに表示する] リンク")

8. [**属性を収集する**] には以下を指定します。

    - **国/地域**
    - **表示名**
    - **郵便番号**

9. [**要求を返す**] には以下を指定します。

    - **表示名**
    - **ID プロバイダー**
    - **郵便番号**
    - **新しいユーザー**
    - **ユーザーのオブジェクト ID**
  
10. 選択内容を確認して [**OK**] をクリックします。

    ![[Azure AD B2C - ユーザー フロー] の [属性を収集する] 列と [要求を返す] 列を確認する](media/2019-03-28-12-44-04.png "属性の収集と要求の応答")

11. [**作成**] をクリックします。先ほど作成したポリシーが [**サインアップ ポリシー**] ブレードに **B2C\_1\_SignUp** (**B2C\_1\_** の部分は自動的に追加) という名前で表示されていることを確認します。

    >**注**: ポリシー作成後このページの更新や読み込みには数分程度かかります。

    ![[Azure AD B2C - ユーザー フロー] のリスト。  新規作成されたフローが表示されている](media/2019-03-28-12-46-48.png "[Azure AD B2C - ユーザー フロー] のリスト")

12. リストから **B2C\_1\_SignUp** などを選択すると、ポリシーが開きます。

13. [**ユーザー フローを実行します**] を選択すると、ダイアログが表示されます。
    ![ポリシー セクションでサインイン ポリシーが選択されている](media/2019-03-28-12-52-27.png "ポリシー セクション")

14. [**ユーザー フローを実行します**] を選択し、アプリケーションを指定してユーザー フローを実行します。 

    ![アプリケーション選択オプションが表示されている。Contoso B2C Application というオプションが選択されている。[ユーザー フローを実行します] ボタンが表示されている](media/2019-03-28-12-55-51.png "ユーザー フローのテスト")

15. ブラウザーのタブまたはウィンドウに以下のスクリーンショットのような画面が表示されます。

    ![ユーザー フローのテスト。  ブラウザーにサンプルのサインイン情報が表示されている](media/2019-03-28-13-00-01.png "ユーザー フローのテスト")
    
16. [**今すぐサインアップ**] を選択します。

    ![[今すぐサインアップ] フィールドが表示されている](media/2019-03-28-13-02-25.png "[今すぐサインアップ]")

### タスク 4: プロファイル編集ポリシーを作成する<a name="タスク-4:-プロファイル編集ポリシーを作成する"></a>

アプリケーションでプロファイルを編集できるようにするためには、プロファイル編集ポリシーを作成する必要があります。このポリシーは、一般ユーザーがプロファイルを編集するときのユーザー エクスペリエンスと、編集完了時にアプリケーションに送られるトークンの内容を示します。

1. 左側のブレードの [**ユーザー フロー**] リンクを選択します。

2. ブレード上部の [**+ 新しいユーザー フロー**] リンクを選択します。

3. [**すべて**] タブ リンクを選択します。

    ![[ユーザー フローを作成する] ウィンドウが表示されている。  [すべて] タブが選択されている。すべてのユーザー フローが表示されている。[プロファイルの編集] が矢印で指し示されている](media/2019-03-28-16-19-55.png "[プロファイルの編集] を選択")

4. [**プロファイルの編集**] を選択します。

5. [名前] フィールドに、アプリケーションで使用されるプロファイル編集ポリシー名を入力します。ここでは「**EditProfile**」と入力します。

    ![[ポリシーの追加] ブレードで ID プロバイダー (1 つが選択されている) が選択されている。[ID プロバイダー] では [ローカル アカウント サインイン] が選択されている](media/2019-03-28-16-24-26.png "[ローカル アカウント サインイン] を選択")

6. [ID プロバイダー]、[**ローカル アカウント サインイン**] の順に選択します。

7. [**さらに表示する...**] リンクを選択します。

8. [**属性を収集する**] を選択します。ここでは、ユーザーが表示や編集をできるようにする属性を選択します。

    今回は以下の項目を選択します。

    - **国/地域**
    - **表示名**
    - **役職**
    - **郵便番号**
    - **都道府県**
    - **番地**

9. [**要求を返す**] を選択します。選択した要求は、プロファイル編集完了時にアプリケーションに送り返されるトークンとして戻されます。

    今回は以下の項目を選択します。

    - **表示名**
    - **郵便番号**

    ![[サインアップ] のユーザー属性選択ブレード](media/2019-03-28-16-28-53.png "[サインアップ] のユーザー属性選択ブレード")

10. [**OK**] を選択します。

11. [**作成**] をクリックします。先ほど作成したポリシーが [**プロファイル編集ポリシー**] ブレードに **B2C\_1\_EditProfile** \(**B2C\_1\_** の部分は自動的に追加) という名前で表示されていることを確認します。

12. **B2C\_1\_EditProfile** を選択してポリシーを開き、[**ユーザー フローを実行する**] をクリックします。

13. [**アプリケーションの選択**] ドロップダウン リストで **Contoso B2C application** を選択します。

14. [**ユーザー フローを実行する**] をクリックします。ブラウザーの新規タブを開くと、アプリケーションのプロファイル編集の一般ユーザー用エクスペリエンスを実行できます。

### タスク 5: パスワード リセット ポリシーを作成する<a name="タスク-5:-パスワード-リセット-ポリシーを作成する"></a>

アプリケーションでプロファイルを編集できるようにするためには、プロファイルのパスワード リセットポリシーを作成する必要があります。このポリシーは、一般ユーザーがパスワードをリセットするときのユーザー エクスペリエンスと、リセット完了時にアプリケーションに送られるトークンの内容を示します。

1. 左側のブレードの [**ユーザー フロー**] リンクを選択します。

2. ブレード上部の [**+ 新しいユーザー フロー**] リンクを選択します。

3. [**パスワードのリセット**] を選択します。

    ![[ユーザー フローを作成する] ウィンドウが表示されている。  [推奨] タブが選択されている。[パスワードのリセット] が強調表示されている](media/2020/03/19-09-47-15.png "[パスワードのリセット] を選択")

4. [名前] フィールドに、アプリケーションで使用されるプロファイル編集ポリシー名を入力します。ここでは「**SSPR**」と入力します。

    ![[ポリシーの追加] ブレードで ID プロバイダー (1 つが選択されている) が選択されている [ID プロバイダー] では [電子メール アドレスを使用したパスワードのリセット] が選択されている](media/2020-03-19-09-50-24.png "[電子メール アドレスを使用したパスワードのリセット] を選択")

5. ID プロバイダーを選択してから [**電子メール アドレスを使用したパスワードのリセット**] を選択します。

6. [**さらに表示する...**] リンクを選択します。

7. [**要求を返す**] を選択します。ここで選択したユーザー属性は、トークンでアプリケーションに返されます。

    ここでは以下の項目を選択します。

    - **電子メール アドレス**
    - **名**

    ![[要求を返す] の属性選択ブレード](media/2020-03-19-09-54-28.png "[要求を返す]")

8. [**OK**] を選択します。

9. [**作成**] をクリックします。作成されたポリシーが [**プロファイル編集ポリシー**] ブレードに **B2C\_1\_SSPR** \(**B2C\_1\_** の部分は自動的に追加) という名前で表示されていることを確認します。

10. **B2C\_1\_SSPR** を選択してポリシーを開き、[**ユーザー フローを実行する**] をクリックします。

11. [**アプリケーションの選択**] ドロップダウン リストで **Contoso B2C application** を選択します。

12. [**ユーザー フローを実行する**] をクリックします。ブラウザーの新規タブを開くと、アプリケーションのプロファイル編集の一般ユーザー用エクスペリエンスを実行できます。

### タスク 6: Contoso.App.SportsLeague.Web を変更する<a name="タスク-6:-Contoso.App.SportsLeague.Web-を変更する"></a>

1. **Contoso.Apps.SportsLeague.Web** プロジェクトを展開します。**Startup.cs** というコード ファイルで `public void ConfigureServices(` メソッド宣言を探し、メソッド末尾に次のコード行を追加します。

    ```csharp
    services.AddAuthentication(Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults.AuthenticationScheme)
                .AddAzureADB2C(options => Configuration.Bind("AzureADB2C", options));
    ```

    ![Startup.cs ファイルの "AddAuthentication();" の部分が強調表示されている](media/2019-04-19-15-08-40.png "Startup.cs")

2. 次の `using` ディレクティブを **Startup.cs** コード ファイルの冒頭に追加します。

    ```
    using Microsoft.AspNetCore.Authentication;
    using Microsoft.AspNetCore.Authentication.AzureADB2C.UI;
    ```

3. `public void Configure` メソッドの `app.UseAuthentication();` という行を探し、その後に以下の行を追加します。

    ```
    app.UseAuthentication();
    app.UseAuthorization();
    ```

    上記の手順の結果、以下のようになります。

    ![app.UseAuthentication というコードが挿入されている](media/2020-03-18-14-44-13.png "app.UseAuthentication というコードの挿入")

4. リソース グループから Azure AD B2C の名前を探します。その名前をメモ帳にコピーします。

    ![ContosoSports リソース グループ内のすべてのリソースのリスト。B2C のテナント名が矢印で指し示されている](media/2019-03-28-16-51-14.png "B2C のテナント名を探す")

5. 次に、Azure 管理ポータルからメインのサブスクリプションを使用して Contoso Web アプリのブレードを開き、[**構成**] を選択します。

6. [**アプリケーション設定**] セクションで、以下のように設定します。

   - AzureADB2C:Instance - `https://[your Azure AD B2C name].b2clogin.com/tfp/`.
   - AzureADB2C:ClientId - **先にコピーした B2C アプリケーションの ID**
   - AzureADB2C:CallbackPath - `/signin-oidc-b2c`
   - AzureADB2C:Domain - **[使用する Azure AD B2C 名].onmicrosoft.com**.
   - AzureADB2C:SignUpSignInPolicyId - `B2C_1_SignUp`
   - AzureADB2C:ResetPasswordPolicyId - `B2C_1_SSPR`
   - AzureADB2C:EditProfilePolicyId - `B2C_1_EditProfile`

7. 設定が完了したら [**保存**] をクリックします。

### タスク 7: 認証要求を Azure AD に送信する<a name="タスク-7:-認証要求を-Azure-AD-に送信する"></a>

アプリケーションが正しく構成され、ASP.NET Core Identity を使用して Azure AD B2C と通信できるようになりました。認証メッセージの作成、Azure AD からのトークンの検証、ユーザー セッションの保持などの詳細はすべて OWIN が担当します。あとは各ユーザーのフローを開始するだけです。

1. **Controllers** フォルダー、[**追加**]、[**コントローラー**] の順に選択します。

    ![ソリューション エクスプローラーで Controllers フォルダーの右クリック メニューから [追加] が選択され、さらにそのメニューから [コントローラー] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image177.png "ソリューション エクスプローラー")

2. [**MVC コントローラー - 空**]、[**追加**] の順に選択します。[**コントローラーの追加**] ダイアログ ボックスで **DefaultController** の値を **AccountController** に変更します。

    ![[スキャフォールディングを追加] ウィンドウの左側で [インストール済み]、[コントローラー] が選択されている。ウィンドウ中央では [MVC コントローラー - 空] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image178.png "[スキャフォールディングを追加] ウィンドウ")

3. 以下の using 文をコントローラーの冒頭に追加します。

    ```csharp
    using Microsoft.AspNetCore.Authentication;
    using Microsoft.AspNetCore.Authentication.AzureADB2C.UI;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    ```

4. 既定のコントローラーの **Index** メソッドを探します。

    ![既定のコントローラーの Index メソッドが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image179.png "既定のコントローラーの Index")

    このメソッドを以下のコードに変更し、[**保存**] をクリックしてファイルを保存します。

    ```csharp
    // Controllers\AccountController.cs

    private string _editProfilePolicyId;

    public AccountController(IConfiguration configuration)
    {
        _editProfilePolicyId = configuration.GetValue<string>("AzureADB2C:EditProfilePolicyId");
    }

    public ActionResult SignIn()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return Challenge(new AuthenticationProperties() { RedirectUri = "/" }, AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }
            
    public ActionResult SignUp()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return Challenge(new AuthenticationProperties() { RedirectUri = "/" }, AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }

    public ActionResult Profile()
    {
        if (User.Identity.IsAuthenticated)
        {
                var properties = new AuthenticationProperties() { RedirectUri = "/" };
                properties.Items[AzureADB2CDefaults.PolicyKey] = _editProfilePolicyId;
                return Challenge(
                    properties,
                    AzureADB2CDefaults.AuthenticationScheme);
        }
        return RedirectToAction("Index", "Home");
    }

    public ActionResult SignOut()
    {
        if (!User.Identity.IsAuthenticated)
        {
            return RedirectToAction("Index", "Home");
        }
        string redirectUri = Url.Action("Index", "Home", null, Request.Scheme);
        var properties = new AuthenticationProperties
        {
            RedirectUri = redirectUri
        };
        return SignOut(properties, AzureADB2CDefaults.CookieScheme, AzureADB2CDefaults.OpenIdScheme);
    }
    ```

5. ファイルを保存します。

### タスク 8: ユーザー情報を表示する<a name="タスク-8:-ユーザー情報を表示する"></a>

ユーザー認証に OpenID Connect を使用する場合、Azure AD は**要求**を含む ID トークンをアプリケーションに返します。これは、ユーザーに関するアサーションです。要求は、アプリケーションのパーソナライズに使用できます。コントローラーに含まれるユーザーの要求には、ClaimsPrincipal.Current セキュリティ プリンシパル オブジェクトでアクセスできます。

1. **Controllers\\HomeController.cs** ファイルを開き、ファイル冒頭部分の using 文の後に以下の using 文を追加します。

    ```csharp
    using Contoso.Apps.SportsLeague.Web.Models;
    using Microsoft.AspNetCore.Authorization;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    ```

2. さらに、**Controllers\\HomeController.cs** ファイルの **HomeController** クラスに以下のメソッドを追加します。

    ```csharp
    [Authorize]
    public ActionResult Claims()
    {
        var displayName = User.Identity.Name;
        ViewBag.DisplayName = displayName;
        ViewBag.Claims = User.Claims;
        return View();
    }
    ```

3. 同じ方法で、アプリケーションに送られるあらゆる要求にアクセスできます。アプリケーションに送られる要求がすべて掲載されたリストは、[**要求**] ページで確認できます。Visual Studio で Contoso.Apps.SportsLeague.Web オブジェクトを表示し、右クリックして [**ビュー**]、**Home** フォルダー、[**追加**]、[**ビュー**] の順に選択し、「**Claims**」と命名します。  [**OK**] を選択します。

    ![ソリューション エクスプローラーの右クリック メニューで [ビュー]、Home フォルダー、[追加] の順に選択され、[ビュー] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180.png "ソリューション エクスプローラー")

4. **Claims.cshtml** ファイルを開き、コードを以下のように変更します。

    ```csharp
    @using System.Security.Claims
    @{
        ViewBag.Title = "Claims";
    }
    <h2>@ViewBag.Title</h2>

    <h4>Claims Present in the Claims Identity: @ViewBag.DisplayName</h4>

    <table class="table-hover claim-table">
        <tr>
            <th class="claim-type claim-data claim-head">Claim Type</th>
            <th class="claim-data claim-head">Claim Value</th>
        </tr>

        @foreach (Claim claim in ViewBag.Claims)
        {
            <tr>
                <td class="claim-type claim-data">@claim.Type</td>
                <td class="claim-data">@claim.Value</td>
            </tr>
        }
    </table>
    ```

5. [**ビュー**] を右クリックして **Shared** フォルダー、[**追加**] を選択し、[**ビュー**] を新規追加して、[**部分ビューとして作成する**] に設定します。「**\_LoginPartial**」と命名します。

    ![ソリューション エクスプローラーの右クリック メニューで [ビュー]、Shared フォルダー、[追加] の順に選択され、[ビュー] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180.png "ソリューション エクスプローラー")

    ![[部分ビューとして作成する] が強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image180-b.png "MVC ビューの追加")

6. Razor の部分ビューに以下のコードを追加し、サインイン、サインアウト、ユーザー プロファイル編集のリンクを作成します。

    ```html
    @if (User.Identity.IsAuthenticated)
    {
        <text>
            <ul class="nav navbar-nav navbar-right">
                <li>
                    <a id="profile-link">@User.Identity.Name</a>
                    <div id="profile-options" class="nav navbar-nav navbar-right">
                        <ul class="profile-links">
                            <li class="profile-link">
                                @Html.ActionLink("Edit Profile", "Profile", "Account")
                            </li>
                        </ul>
                    </div>
                </li>
                <li>
                    @Html.ActionLink("Sign out", "SignOut", "Account")
                </li>
            </ul>
        </text>
    }
    else
    {
        <ul class="nav navbar-nav navbar-right">
            <li>@Html.ActionLink("Sign up", "SignUp", "Account", routeValues: null, htmlAttributes: new { id = "signUpLink" })</li>
            <li>@Html.ActionLink("Sign in", "SignIn", "Account", routeValues: null, htmlAttributes: new { id = "loginLink" })</li>
        </ul>
    }
    ```

7. Visual Studio で [**ビュー**]、**Shared** フォルダー、**_Layout.cshtml** の順に選択します。header-top div を検索し、**@Html.ActionLink** から始まる行、および **@Html.Partial** から始まる行を追加します。

    ```html
    <div class="header-top">
        <div class="container">
            <div class="row">
                <div class="header-top-left">
                <a href="#"><i class="fa fa-twitter"></i></a>
                <a href="#"><i class="fa fa-facebook"></i></a>
                <a href="#"><i class="fa fa-linkedin"></i></a>
                <a href="#"><i class="fa fa-instagram"></i></a>
                </div>
                <div class="header-top-right">
                    <a href="#" class="top-wrap"><span class="icon-phone">Call today: </span> (555) 555-8000</a>
                    @Html.ActionLink("Claims", "Claims", "Home")
                </div>
                @Html.Partial("_LoginPartial")
            </div>
        </div>
    </div>
    ```

### タスク 9: サンプル アプリを実行する<a name="タスク-9:-サンプル-アプリを実行する"></a>

1. **Contoso.Apps.SportsLeague.Web** プロジェクトを右クリックして [**発行**] を選択します。以下の手順で、更新したアプリケーションを Microsoft Azure Web Apps にデプロイします。

    Visual Studio 外部でブラウザーを起動し、ページが Visual Studio に読み込まれるかどうかをテストします。

2. サインアップ テストを行います。

3. 次に、サインアウト テストを行います。

4. サインインしていない状態で [要求] を選択すると、サインイン ページに移動し、その後に要求の情報が表示されます。サインインしてプロファイル編集のテストを行います。

    ![Contoso の Web サイトで [要求]、[サインアップ]、[サインイン] のリンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image182.png "Contoso の Web サイト")

    要求情報ページは以下のようになります。![Contoso の Web サイトで [Russell]、[サインイン]、[サインアウト]、[プロファイルの編集] が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image183.png "Contoso の Web サイト、要求情報ページ")

<!--
## Exercise 4: Enabling Telemetry with Application Insights

Duration: 30 Minutes

To configure the application for logging and diagnostics, you have been asked to configure Microsoft Azure Application Insights and add some custom telemetry.

### Task 1: Configure the application for telemetry

#### Subtask 1: Add Application Insights Telemetry to the e-commerce website project

1. Open the Solution **Contoso.Apps.SportsLeague** in Visual Studio.

2. Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

3. Expand the **Contoso.Apps.SportsLeague.Web** project, then right-click on the **Dependencies** node, and select **Manage NuGet Packages...**.

4. Within the **NuGet Package Manager**, select the **Browse** tab, then search for and install the following NuGet package:

    - **Microsoft.ApplicationInsights**
    - **Microsoft.ApplicationInsights.Web**

5. Open the file `\Helpers\TelemetryHelper.cs` located in the **Contoso.Apps.SportsLeague.Web** project.

6. Add the following using statement to the top of the file:

    ```csharp
    using Microsoft.ApplicationInsights;
    ```

7. Add the following code to the **TrackException** method to instantiate the telemetry client and track exceptions:

    ```csharp
    var client = new TelemetryClient();
    client.TrackException(new Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry(exc));
    ```

8. Add the following code to the **TrackEvent** method to instantiate the telemetry client and track event data:

    ```csharp
    var client = new TelemetryClient();
    client.TrackEvent(eventName, properties);
    ```

9. Save the `TelemetryHelper.cs` file.

#### Subtask 2: Enable client side telemetry

1. Open the Azure Management Portal (<http://portal.azure.com>), and navigate to the **contososports** Resource Group.

2. Select the **Application Insights** instance with the name that starts with **contososportsai** that is associated with the Contoso E-Commerce Site.

3. Capture the **Instrumentation Key**.

    - Select the **Overview** menu item.
    - Copy the **Instrumentation Key** to Notepad for later use.

    ![Contoso.Apps.SportsLeague Application Insights Overview. Instrumentation Key selected.](media/2019-03-29-10-36-23.png "Instrumentation Key selected")

4. In the tiles up top, select **Getting Started**.

    ![From the Configure menu, Getting started is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image196.png "Configure menu")

5. In the portal, navigate to **How-to Guides** -> **Application Insights** -> **Code-based monitoring** -> **Web pages** -> **Client-side JavaScript**, then navigate to the **Snippet based setup** section under **Adding the JavaScript SDK** within the documentation page.

    ![Screenshot of the MONITOR AND DIAGNOSE CLIENT SIDE APPLICATION arrow.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image197.png "MONITOR AND DIAGNOSE CLIENT SIDE APPLICATION ")

    > **Note**: You can find the documentation page at the following URL: <https://docs.microsoft.com/azure/azure-monitor/app/javascript#snippet-based-setup>.

6. Select and copy the full contents of the JavaScript under the **Snippet based setup** heading.

    ![Under Guidance in the Client application monitoring and diagnosis blade, JavaScript displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image198.png "Client application monitoring and diagnosis blade")

    Here's the JavaScript code to copy/paste for quick reference:

    ```javascript
    <script type="text/javascript">
    var sdkInstance="appInsightsSDK";window[sdkInstance]="appInsights";var aiName=window[sdkInstance],aisdk=window[aiName]||function(n){var o={config:n,initialize:!0},t=document,e=window,i="script";setTimeout(function(){var e=t.createElement(i);e.src=n.url||"https://az416426.vo.msecnd.net/scripts/b/ai.2.min.js",t.getElementsByTagName(i)[0].parentNode.appendChild(e)});try{o.cookie=t.cookie}catch(e){}function a(n){o[n]=function(){var e=arguments;o.queue.push(function(){o[n].apply(o,e)})}}o.queue=[],o.version=2;for(var s=["Event","PageView","Exception","Trace","DependencyData","Metric","PageViewPerformance"];s.length;)a("track"+s.pop());var r="Track",c=r+"Page";a("start"+c),a("stop"+c);var u=r+"Event";if(a("start"+u),a("stop"+u),a("addTelemetryInitializer"),a("setAuthenticatedUserContext"),a("clearAuthenticatedUserContext"),a("flush"),o.SeverityLevel={Verbose:0,Information:1,Warning:2,Error:3,Critical:4},!(!0===n.disableExceptionTracking||n.extensionConfig&&n.extensionConfig.ApplicationInsightsAnalytics&&!0===n.extensionConfig.ApplicationInsightsAnalytics.disableExceptionTracking)){a("_"+(s="onerror"));var p=e[s];e[s]=function(e,n,t,i,a){var r=p&&p(e,n,t,i,a);return!0!==r&&o["_"+s]({message:e,url:n,lineNumber:t,columnNumber:i,error:a}),r},n.autoExceptionInstrumented=!0}return o}(
    {
    instrumentationKey:"INSTRUMENTATION_KEY"
    }
    );(window[aiName]=aisdk).queue&&0===aisdk.queue.length&&aisdk.trackPageView({});
    </script>
    ```

    >**Note**: Make sure to replace the `INSTRUMENTATION_KEY` placeholder with the Application Insights Instrumentation Key.

7. Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

8. Open **Views \> Shared \> \_Layout.cshtml**.

    ![In Solution Explorer, under Views\\Shared, Layout.cshtml is selected](media/2019-04-19-15-45-29.png "Solution Explorer")

9. Paste in the code before the `</head>` tag. Insert your **Instrumentation Key** from Notepad into the JavaScript code ``instrumentationKey:`` value.

    ![In Layout.cshtml, code displays, and several lines are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image200.png "Layout.cshtml tab")

10. Save the **\_Layout.cshtml** file.

#### Subtask 3: Deploy the e-commerce Web App from Visual Studio

1. Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

2. Right-click on the **Contoso.Apps.SportsLeague.Web** project, and select **Publish**.

    ![From the Contoso.Apps.SportsLeague.Web right-click menu, Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image202.png "Solution Explorer")

3. Select **Publish** again when the Publish dialog appears.

    Launch a browser **outside of Visual Studio** for testing if the page is loaded in Visual Studio.

4. Select a few links on the published E-Commerce website, and submit several orders to generate some sample telemetry.

### Task 2: Creating the web performance test and load test

#### Subtask 1: Create the load test

1. Open the Azure Management Portal (<http://portal.azure.com>), and navigate to the **contososports** Resource Group.

2. Select the **Application Insights** instance with the name that starts with **contososportsai** that is associated with the Contoso E-Commerce Site.

3. Select **Performance Testing**.

    ![On the Configure menu, Performance Testing is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image205.png "Configure menu")

4. Select the **Set Organization** button to associate/create an Azure DevOps account.

    ![On the Application Insights blade, Set Organization is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image206.png "Application Insights blade")

5. On the Organization Settings tile, select the **Or Create New** link.

    ![On the Organization Settings tile, the Or Create New link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image207.png "Account tile")

6. Specify a unique name for the account and select a region.

    >**Note**: The region may differ from the region you have deployed your resources.

    ![On the Organization Settings blade, under Azure DevOps Account, contososportsis selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image208.png "Account Settings blade")

7. Select **Subscription**, and select **your Subscription**.

    ![The Subscription option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image209.png "Subscription option")

8. Choose **Select location**. Next, select a Location.

    ![The Select location option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image210.png "Select location option ")

    >**Note**: The location tile may disappear after setting your Subscription.

9. Then, select **OK**.

    >**Note**: The Azure DevOps account creation will take a minute to complete.

10. Select **New**.

    ![On the Application Insights blade, the New button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image211.png "Application Insights blade")

11. Select **Configure Test Using**.

    ![The Configure Test Using option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image212.png "Configure Test Using option")

12. Specify the **URL** to the Contoso E-Commerce site, and select **Done**.

    ![In the Configure test using blade, the https://contososportsweb3.azurewebsites URL is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image213.png "Configure test using")

13. Name the test **ContosoSportsTest**, and select the **Run test** button.

    ![On the New performance test blade, under Name, ContosoSportsTest is selected. At the bottom, the Run test button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image214.png "New performance test blade")

14. Wait until the load test has completed. This may take 5-10 minutes.

    ![In the Recent runs section, the load test for ContosoSportsTest has a state of Completed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image215.png "Recent runs section")

#### Subtask 2: View the Application Insights logs

1. Using a new tab or instance of your browser, navigate to the Azure Management portal <http://portal.azure.com>.

2. On the left menu area, select **All services**.

3. On the **All Services** blade, filter for **Application Insights** and choose the appropriate result.

4. On the **Application Insights** blade, select the Application Insights configuration you created for the e-commerce website.

    ![The Application Insights configuration option Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image216.png "Application Insights configuration option")

5. Select **Application Dashboard**.  View the performance timeline to see the overall number of requests and page load time.

    ![Application Insights - Contoso.Apps.SportsLeague.Web - At the top of the page, the Application Dashboard link is highlighted and has an arrow pointing to it. Failed requests and server response metrics are displayed.](media/2019-03-29-11-10-04.png "Click the Dashboard link")

    ![The Contoso web metrics are displayed. Usage, reliability, and responsiveness graphs are displayed.](media/2019-03-29-11-12-13.png "Application Insights Default Dashboard")

6. Navigate back to the Application Insights overview for ``Contoso.Apps.SportsLeague.Web``. Select **Performance** to see individual endpoint render performance.
  
    ![Contoso.Apps.SportsLeague.Web Performance link selected.](media/2019-03-29-11-01-14.png "Performance link selected")

    ![Contoso.Apps.SportsLeague.Web Performance - Endpoint performance metrics are displayed for various types of HTTP requests.](media/2019-03-29-11-20-06.png "Endpoint performance")

7. Under **Usage** link area, select the **Events** menu option. Select the **View More Insights** button.

    ![A screenshot using the Events button under the Usage Preview section.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image218.png "The Usage Preview section")

8. Select **View More Insights**, then scroll down to see event list.

    ![In the Custom events section, event metrics are displayed for users and sessions. Different web pages are listed. e.g. OrderCompleted and SuccessfulPaymentAuth.](media/2019-03-29-11-35-33.png "Event Statistics")

-->
## 演習 4: Application Insights でテレメトリを有効化する<a name="演習-4:-Application-Insights-でテレメトリを有効化する"></a>

アプリケーションでログの記録や診断を行う場合、Microsoft Azure Application Insights を構成し、カスタム テレメトリをいくつか追加する必要があります。

### タスク 1: アプリケーションでテレメトリを構成する<a name="タスク-1:-アプリケーションでテレメトリを構成する"></a>

#### サブタスク 1: eコマース Web サイト プロジェクトに Application Insights Telemetry を追加する<a name="サブタスク-1:-eコマース-Web-サイト-プロジェクトに-Application-Insights-Telemetry-を追加する"></a>

1. Visual Studio で **Contoso.Apps.SportsLeague** というソリューションを開きます。

2. Visual Studio の**ソリューション エクスプローラー**で **Web** フォルダーの **Contoso.Apps.SportsLeague.Web** プロジェクトに移動します。

3. **Contoso.Apps.SportsLeague.Web** プロジェクトを展開し、[**相互関係**] ノードを右クリックして [**NuGet パッケージの管理...**] を選択します。

4. **NuGet パッケージ マネージャー**で [**参照**] タブを選択し、以下の NuGet パッケージを検索してインストールします。

    - **Microsoft.ApplicationInsights**
    - **Microsoft.ApplicationInsights.Web**

5. **Contoso.Apps.SportsLeague.Web** プロジェクトの `\Helpers\TelemetryHelper.cs` ファイルを開きます。

6. 以下の using 文をファイルの冒頭に追加します。

    ```csharp
    using Microsoft.ApplicationInsights;
    ```

7. **TrackException** メソッドに以下のコードを追加します。このコードはテレメトリ クライアントのインスタンス化と例外の追跡を実行します。

    ```csharp
    var client = new TelemetryClient();
    client.TrackException(new Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry(exc));
    ```

8. **TrackEvent** メソッドに以下のコードを追加します。このコードはテレメトリ クライアントのインスタンス化とイベント データの追跡を実行します。

    ```csharp
    var client = new TelemetryClient();
    client.TrackEvent(eventName, properties);
    ```

9. `TelemetryHelper.cs` ファイルを保存します。

#### サブタスク 2: クライアント側のテレメトリを有効化する<a name="サブタスク-2:-クライアント側のテレメトリを有効化する"></a>

1. Azure 管理ポータル (<http://portal.azure.com>) を開き、**contososports** リソース グループに移動します。

2. Contoso の eコマース サイトに関連付けられている、**contososportsai** で始まる名前の **Application Insights** インスタンスを選択します。

3. **インストルメンテーション キー**を取得します。
       - [**概要**] メニュー アイテムを選択します。
       - 後で使用するため、**インストルメンテーション キー**をメモ帳にコピーします。

    ![Contoso.Apps.SportsLeague Application Insights の概要。インストルメンテーション キーが選択されている](media/2019-03-29-10-36-23.png "インストルメンテーション キーが選択されている")

4. 最上部にある [**作業の開始**] タイルを選択します。

    ![[構成] メニューで [作業の開始] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image196.png "[構成] メニュー")

5. ポータルで [**操作方法ガイド**]、[**Application Insights**]、[**コードベースの監視**]、[**Web ページ**]、[**クライアント側の JavaScript**] の順に選択し、ドキュメント ページの「**JavaScript SDK を追加する**」の「**スニペット ベースのセットアップ**」セクションに移動します。

    ![クライアント側アプリケーションの監視と診断の項目を示す矢印のスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image197.png "クライアント側アプリケーションの監視と診断")

    > **注**: このドキュメントは以下の URLからアクセスできます。
<https://docs.microsoft.com/azure/azure-monitor/app/javascript#snippet-based-setup>

6. 「**スニペット ベースのセットアップ**」という項目に掲載されている JavaScript 全文をコピーします。

    ![クライアント アプリケーションの監視と診断に関するガイドのブレードに JavaScript が表示されている。](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image198.png "クライアント アプリケーションの監視と診断に関するブレード")

    上記の JavaScript コードは、以下からもコピー アンド ペーストできます。

    ```javascript
    <script type="text/javascript">
    var sdkInstance="appInsightsSDK";window[sdkInstance]="appInsights";var aiName=window[sdkInstance],aisdk=window[aiName]||function(n){var o={config:n,initialize:!0},t=document,e=window,i="script";setTimeout(function(){var e=t.createElement(i);e.src=n.url||"https://az416426.vo.msecnd.net/scripts/b/ai.2.min.js",t.getElementsByTagName(i)[0].parentNode.appendChild(e)});try{o.cookie=t.cookie}catch(e){}function a(n){o[n]=function(){var e=arguments;o.queue.push(function(){o[n].apply(o,e)})}}o.queue=[],o.version=2;for(var s=["Event","PageView","Exception","Trace","DependencyData","Metric","PageViewPerformance"];s.length;)a("track"+s.pop());var r="Track",c=r+"Page";a("start"+c),a("stop"+c);var u=r+"Event";if(a("start"+u),a("stop"+u),a("addTelemetryInitializer"),a("setAuthenticatedUserContext"),a("clearAuthenticatedUserContext"),a("flush"),o.SeverityLevel={Verbose:0,Information:1,Warning:2,Error:3,Critical:4},!(!0===n.disableExceptionTracking||n.extensionConfig&&n.extensionConfig.ApplicationInsightsAnalytics&&!0===n.extensionConfig.ApplicationInsightsAnalytics.disableExceptionTracking)){a("_"+(s="onerror"));var p=e[s];e[s]=function(e,n,t,i,a){var r=p&&p(e,n,t,i,a);return!0!==r&&o["_"+s]({message:e,url:n,lineNumber:t,columnNumber:i,error:a}),r},n.autoExceptionInstrumented=!0}return o}(
    {
    instrumentationKey:"INSTRUMENTATION_KEY"
    }
    );(window[aiName]=aisdk).queue&&0===aisdk.queue.length&&aisdk.trackPageView({});
    </script>
    ```

    >**注**: `INSTRUMENTATION_KEY` というプレースホルダーは、Applicaiton Insights のインストルメンテーション キーに変更します。

7. Visual Studio の**ソリューション エクスプローラー**で **Web** フォルダーの **Contoso.Apps.SportsLeague.Web** プロジェクトに移動します。

8. [**ビュー**]、**Shared** フォルダー、**_Layout.cshtml** の順に選択します。

    ![ソリューション エクスプローラーで [ビュー]、Shared フォルダー、Layout.cshtml が選択されている](media/2019-04-19-15-45-29.png "ソリューション エクスプローラー")

9. コードを `</head>` タグの前に貼り付けます。メモ帳にコピーした**インストルメンテーション キー**を JavaScript コードの ``instrumentationKey:`` の値として挿入します。

    ![Layout.cshtml のコードの中の数行が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image200.png "Layout.cshtml タブ")

10. **\_Layout.cshtml** ファイルを保存します。

#### サブタスク 3: Visual Studio から eコマース Web アプリをデプロイする<a name="サブタスク-3:-Visual-Studio-から-eコマース-Web-アプリをデプロイする"></a>


1. Visual Studio の**ソリューション エクスプローラー**で **Web** フォルダーの **Contoso.Apps.SportsLeague.Web** プロジェクトに移動します。

2. **Contoso.Apps.SportsLeague.Web** プロジェクトを右クリックして [**発行**] を選択します。

    ![Contoso.Apps.SportsLeague.Web の右クリック メニューで [発行] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image202.png "ソリューション エクスプローラー")

3. [発行] ダイアログが表示されたら、再度 [**発行**] を選択します。

    Visual Studio にページが読み込まれたら、テスト用のブラウザーを **Visual Studio の外部**で開きます。

4. 発行された eコマース Web サイトで、リンクを選択して注文を何度か行い、テレメトリのサンプルを生成します。

### タスク 2: Web のパフォーマンス テストと負荷テストを作成する<a name="タスク-2:-Web-のパフォーマンス-テストと負荷テストを作成する"></a>

#### サブタスク 1: 負荷テストを作成する<a name="サブタスク-1:-負荷テストを作成する"></a>

1. Azure 管理ポータル (<http://portal.azure.com>) を開き、**contososports** リソース グループに移動します。

2. Contoso の eコマース サイトに関連付けられている、**contososportsai** で始まる名前の **Application Insights** インスタンスを選択します。

3. [**パフォーマンス テスト**] を選択します。

    ![[構成] メニューで [パフォーマンス テスト] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image205.png "[構成] メニュー")

4. [**組織を設定**] ボタンを選択し、Azure DevOps アカウントを関連付けて作成します。

    ![[Application Insights] ブレードで [組織を設定する] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image206.png "[Application Insights] ブレード")

5. [組織の設定] タイルで [**または新規作成**] リンクを選択します。

    ![[組織の設定] タイルで [または新規作成] リンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image207.png "[アカウント] タイル")

6. アカウントに一意の名前を指定し、リージョンを選択します。

    >**注**: このリージョンは、リソースをデプロイしたリージョンとは異なる場合があります。

    ![[組織の設定] ブレードの Azure DevOps アカウントで contososports が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image208.png "[アカウント設定] ブレード")

7. [**サブスクリプション**] で**自身のサブスクリプション**を選択します。

    ![[サブスクリプション] オプションが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image209.png "[サブスクリプション] オプション")

8. [**場所を選択**] をクリックして、場所を指定します。

    ![[場所を選択] オプションが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image210.png "[場所を選択] オプション")

    >**注**: [場所を設定] タイルは、サブスクリプションを設定すると表示されなくなる場合があります。

9. [**OK**] をクリックします。

    >**注**: Azure DevOps アカウントの作成には 1 分程度かかります。

10. [**新規作成**] を選択します。

    ![[Application Insights] ブレードで [新規作成] ボタンが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image211.png "[Application Insights] ブレード")

11. [**次を使用してテストを構成します**] を選択します。

    ![[次を使用してテストを構成します] オプションが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image212.png "[次を使用してテストを構成します] オプション")

12. Contoso の eコマース サイトの **URL** を指定し、[**完了**] をクリックします。

    ![[次を使用してテストを構成します] ブレードで https://contososportsweb3.azurewebsites という URL が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image213.png "[次を使用してテストを構成します] ブレード")

13. テストを「**ContosoSportsTest**」と命名し、[**テストの実行**] ボタンをクリックします。

    ![[新しいパフォーマンス テスト] ブレードの [名前] で ContosoSportsTest が指定されている。最下部の [テストの実行] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image214.png "[新しいパフォーマンス テスト] ブレード")

14. 負荷テストが完了するまで待機します。5 ～ 10 分程度かかります。

    ![[最近の実行] セクションで負荷テスト「ContosoSportsTest」の状態が [完了] と表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image215.png "[最近の実行] セクション")

#### サブタスク 2: Application Insights のログを表示する<a name="サブタスク-2:-Application-Insights-のログを表示する"></a>

1. ブラウザーの新規タブまたは新規インスタンスで Azure 管理ポータル (<http://portal.azure.com>) を開きます。

2. 左側のメニューから [**すべてのサービス**] を選択します。

3. [**すべてのサービス**] ブレードで「**Application Insights**」で検索し、適切な結果を選択します。

4. [**Application Insights**] ブレードで、eコマース Web サイト用に作成した Application Insights の構成を選択します。

    ![Application Insights の構成オプションで Contoso.Apps.SportsLeague.Web が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image216.png "Application Insights の構成オプション")

5. [**アプリケーション ダッシュボード**] を選択します。  パフォーマンスのタイムラインを表示して、要求の合計数とページの読み込み時間を確認します。

    ![Application Insights、Contoso.Apps.SportsLeague.Web の順に選択され、ページ上部の [アプリケーション ダッシュボード] リンクが強調表示されて、矢印で指し示されている。要求の失敗数とサーバー応答のメトリックが表示されている](media/2019-03-29-11-10-04.png "ダッシュボードのリンクをクリックした様子")

    ![Contoso の Web サイトのメトリックが表示されている。使用状況、信頼性、応答性のグラフが表示されている](media/2019-03-29-11-12-13.png "Application Insights の既定のダッシュボード")

6. ``Contoso.Apps.SportsLeague.Web`` の Application Insights の概要に戻ります。[**パフォーマンス**] を選択して、各エンドポイントのレンダリング パフォーマンスを確認します。
  
    ![Contoso.Apps.SportsLeague.Web の [パフォーマンス] リンクが選択されている](media/2019-03-29-11-01-14.png "[パフォーマンス] リンクを選択")

    ![Contoso.Apps.SportsLeague.Web の [パフォーマンス] でエンドポイントの各種 HTTP 要求のパフォーマンスのメトリックが表示されている](media/2019-03-29-11-20-06.png "エンドポイントのパフォーマンス")

7. [**使用状況**] リンクで [**イベント**] メニュー オプションを選択します。[**その他の分析情報を表示**] ボタンを選択します。

    ![[使用状況 (プレビュー)] セクションで [イベント] ボタンを選択した場合のスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image218.png "[使用状況 (プレビュー)] セクション")

8. [**その他の分析情報を表示**] を選択し、イベント リストを下方向にスクロールします。

    ![[カスタム イベント] セクションでユーザーおよびセッションの各種メトリックが表示されている。OrderCompleted や SuccessfulPaymentAuth など、複数の Web ページがリストに掲載されている](media/2019-03-29-11-35-33.png "イベントの統計")

<!--
## Exercise 5: Automating backend processes with Azure Functions and Logic Apps

Duration: 45 Minutes

Contoso wants to automate the process of generating receipts in PDF format and alerting users when their orders have been processed using Azure Logic App and Functions. To run custom snippets of C\# or node.js in logic apps, you can create custom functions through Azure Functions. [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) offers server-free computing in Microsoft Azure and are useful for performing these tasks:

- Advanced formatting or compute of fields in logic apps

- Perform calculations in a workflow

- Extend the logic app functionality with functions that are supported in C\# or node.js

### Task 1: Create an Azure Function to Generate PDF Receipts

1. Select the **+Create a resource** button found on the upper left-hand corner of the Azure portal and then select **Compute \> Function App**. Select **Create** button at the bottom.

    ![On the left side of the Portal, the Create a resource button is selected. In the middle, under New, Compute is selected. On the right, under Compute, Function App is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image221.png "Azure Portal")

2. Provision and deploy the new function app, with the following settings:

    - **Resource Group**: Use the existing resource group, **contososports**.

    - **Function App name**: _Choose a unique name_.

    - **Publish**: Code

    - **Runtime Stack**: .NET Core.

    - **Region**: _Choose the same region used for the e-commerce web apps in this lab_.

3. Select **Next: Hosting >**.

4. On the **Hosting** tab, select the following values, then select **Review + create**:

    - **Operating System**: Windows

    - **Plan type**: App service plan

    - **Windows Plan**: Choose the App Service Plan used for the e-commerce web app.

5. Select **Create**.

6. Navigate to the Storage Account in the **contososports** resource group, go to **Access Keys** and copy the **Connection String** for the Storage Account. Paste your storage account connection string into Notepad to save for later.

    ![Display storage account list.  Pointing to Access keys.](media/2019-04-15-15-07-15.png "Storage Account Access keys")

7. Navigate to the **Function App** that was just created, and select **Configuration**.

    ![Display Contoso Function App, with the Configuration link highlighted.](media/2019-04-15-15-15-22.png "Contoso Function App Application Settings")

8. Add a new Application Setting with the following values, then select **Save**:

    - **Name**: `contososportsstorage`
    - **Value**: Enter the Connection String for your storage account.

    ![Updated Function App Application settings. Showing final values.](media/2019-04-15-16-18-36.png "Updated Function App Application settings.")

9. To publish the Function App, open the Visual Studio solution, Right-click on the **ContosoFunctionApp** project, then select **Publish**.

    ![Visual Studio Solution Explorer is open. Menu is displayed for Contoso Function App. Selecting function app publish.](media/2019-04-15-15-31-03.png "Selecting function app publish")

10. On the **Pick a publish target** dialog, choose **Select existing**, then select **Create Profile**.

11. Select the **Function App**, then select **OK**.

    ![Azure function app tree displayed. The Contoso Function App is selected.](media/2019-04-15-15-34-54.png "Azure function app tree displayed")

12. Select **Publish**.

    The publish should only take a minute or so. You can check the **Output** window for any errors that may occur.

    ![The build Output window is displayed. Publish succeeded message is shown.](media/2019-04-15-15-33-20.png "Output window.")

13. To test your newly published Function App, start by navigating back to your Contoso Function App in the Azure Portal. Select the newly created **ContosoMakePDF** function listed in the functions.

14. Select the **Test** link located on the right-hand blade.

    ![Function apps are listed on the left hand side. ContosoMakePDF is selected.  There is an arrow pointing to the Test link on the right pane.](media/2019-04-15-15-40-27.png "Function Test link")

15. Select **POST** for the HTTP method.

16. Open the **sample.dat** file found in your lab files Contoso.CreatePDFReport directory.  Copy the contents into the **Request body** text box.

    ![A small screenshot of Windows Explorer is shown emphasizing the file path to the sample.dat file.](media/2019-04-15-15-47-39.png "Sample.dat File")

17. Select the **Run** button located at the bottom of the blade.

    ![The screenshot displays the Test blade with sample.dat contents. The Request body field shows the Order JSON. There is an arrow pointing to Run button.](media/2019-04-15-15-52-59.png "Display Test blade with sample.dat contents")

    > **Note**: There is also a **Run** button located at the top of the Azure Function blade. Selecting either of these buttons will run the function just the same.

    After a few seconds, you should see logs like in the below image. You should see return status code of 200.  The **Output** text box should show recent Contoso purchase data. You should see a message stating the file has been created and stored in the blob storage.

    ![There is a screenshot displaying the Function App test result log.  A status code of 200 OK is displayed on the right side pane.](media/2019-04-15-15-58-54.png "Function App test result log.")

18. Check your receipt PDF in the storage account blob.

    - Navigate to the ContosoSports storage account.
    - Select the **Blobs** link.

    ![The Settings options are displayed. There is an arrow pointing to the Blobs link.](media/2019-04-15-16-06-17.png "Blobs link")

19. Choose the newly created **receipts** blob container.

    ![The storage account blobs are listed. The receipts blob container is highlighted.](media/2019-04-15-16-08-35.png "Click the Blobs link")

20. Open **ContosoSportsLeague-Store-Receipt-XX.pdf** link.

    ![There is a screenshot displaying a list of the newly created PDF receipts. An arrow pointing to the Download link is located on the right side of the screen.](media/2019-04-15-16-11-24.png "PDF Receipts")

21. Open the `...` link and choose download menu item.

    ![A sample Contoso Sports League PDF receipt is displayed.](media/2019-04-15-16-15-06.png "Sample PDF receipt")

### Task 2: Create an Azure Logic App to Process Orders

Without writing any code, you can automate business processes more easily and quickly when you create and run workflows with Azure Logic Apps. Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud. It provides a visual designer to model and automate your process as a series of steps known as a workflow. There are [many connectors](https://docs.microsoft.com/en-us/azure/connectors/apis-list) across the cloud and on-premises to quickly integrate across services and protocols.

The advantages of using Logic Apps include the following:

- Saving time by designing complex processes using easy to understand design tools

- Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code

- Getting started quickly from templates

- Customizing your logic app with your own custom APIs, code, and actions

- Connect and synchronize disparate systems across on-premises and the cloud

- Build off BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support

1. Next, we will create a Logic App that will trigger when an item is added to the **receiptgenerator** queue. In the Azure Management Portal, select the **+Create a resource** button, search for **Logic App**, select the returned Logic App result, and select **Create**.

    ![In the Azure Portal, under Marketplace, Everything is selected. Under Everything, Logic App is in the search field. Under Name, Logic App is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image236.png "Azure Portal")

2. Fill out the name as **ContosoLogicApplication** along with your subscription, and use the existing resource group **contososports**. Choose the **same region** as your Web App and storage account. Select **Create**.

    ![In the Create logic app blade, ContosoLogicApplication is in the Name field. Under Resource group, the Use existing radio button is selected, and contososports is the name.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image237.png "Create logic app blade")

3. Open the logic app after it is deployed by choosing **All Services**, searching for and selecting **Logic App** and selecting the Logic App you just created.

    ![In the Azure Portal, logic is in the search field, and under that, Logic apps is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image238.png "Azure Portal")

4. Select the **Logic App Designer** link.

    ![In the Logic app blade, under Development tools, Logic App Designer is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image239.png "Logic app blade")

5. In the Logic Apps Designer, under **Templates**, select **Blank Logic App**.

    ![In the Logic Apps Designer, the Blank Logic App tile is selected.](media/2019-03-29-12-56-10.png "Logic Apps Designer")

6. Select the **All** tab, then select **Azure Queues**.

    ![In the Services section, the Azure Service Bus tile is selected.](media/2020-03-18-12-12-10.png "Services section")

7. Select **Service Bus - When a message is received in a queue (auto-complete)**.

    ![In the Search all triggers section, Service Bus - When a message is received in a queue (auto-complete).](media/2020-03-18-12-13-24.png "Search all triggers section")

8. Specify **ContosoQueue** as the connection name, select the Contoso storage account from the list, and select **Create**.

    ![In When there are messages in a queue, the Connection Name is ContosoQueue, and under Service Bus Namespace, contosooiyxeonvhew7u is selected.](media/2020-03-18-12-15-23.png "When there are messages in a queue ")

9. Select the **RootManageSharedAccessKey*** from the list of Service Bus Policies, then select **Create**.

    ![RootManageSharedAccessKey is selected.](media/2020-03-18-12-17-17.png "RootManageSharedAccessKey is selected")

10. Select the **receiptgenerator** queue from the drop-down, select **New Step**, and **Add an Action**.

    ![Under When there are messages in a queue, the Queue name is set to receiptgenerator.](media/2020-03-18-12-19-06.png "Queue name")

    >**Note**: If you wish, you can set the **Interval** and **Frequency** to check for new items to a shorter interval than the default; such as every 30 seconds. This could help reduce delay for when the Logic App is triggered when new messages are sent to the Service Bus Queue while you progress through this lab.

11. Select the **+ New step** button, then select **Azure Functions**.

    ![In the Choose an action section, under Services ,the Azure Functions tile is selected.](media/2020-03-18-12-21-44.png "Choose an action")

12. Select the **Azure Function App** you just created.

    ![Under Azure Functions, on the Actions tab, a single Action, the Azure function ContosoFunctionApp, is listed.](media/2020-03-18-12-22-46.png "Azure Functions")

13. Select the Azure function **ContosoMakePDF**.

    ![Under Azure Functions, on the Actions tab, a single Action, the Azure function ContosoMakePDF, is listed.](media/2020-03-18-12-23-39.png "Azure Functions")

14. Type this in the Request Body:

    ```json
    {"Order": pick Content from list }
    ```

    Make sure the syntax is json format. Sometimes the ":" will go to the right side of Content by mistake. Keep it on the left. It should look like this:

    ![Under ContosoMakePDF, the previous JSON code is typed in the Request Body, and to the right of this, in Insert parameters from previous steps, Content is selected.](media/2020-03-18-12-25-29.png "ContosoMakePDF")

15. Select **Save** to save the Logic App.

16. Run the logic app. It should process the orders you have submitted previously to test PDF generation. Using Azure Storage Explorer or Visual Studio Cloud Explorer you can navigate to the storage account and open the receipts container to see the created PDFs.

    ![In Azure Storage Explorer, on the left, the following tree view is expanded: Storage Accounts\\contososportsstorage01r\\Blob Containers. Under Blob Containers, receipts is selected. On the right, the ContosoSportsLeague-Store-Receipt-72.pdf is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image252.png "Azure Storage Explorer")

17. Double-click it to see the Purchase receipt.

18. Now, select the **Designer** button in the Logic Apps Designer screen. add two more steps to the flow for updating the database and removing the message from the queue after it has been processed. Switch back to the designer, select **+ New step**.

    ![In Designer, the New Step link is circled. Under New step, the Add an action tile is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image254.png "Designer")

19. Select **SQL Server**.

    ![In the Services section, under Services, SQL Server is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image255.png "Services section")

20. Select **SQL Server - Update row (V2)**.

    ![In the SQL Server section, on the Actions tab, SQL Server - Update row (V2) is selected.](media/2020-03-18-12-35-07.png "SQL Server section")

21. Enter the following values, then select **Create**:

    - Authentication Type: **SQL Server Authentication**

    - SQL server name: _Enter the DNS name of the SQL Database Failover Cluster Read/Write Listener Endpoint that was copied previously_.

    - SQL database name: `ContosoSportsDB`

    - Username: `demouser`

    - Password: `demo@pass123`

    ![The Update row section displays the previously defined settings.](media/2020-03-18-12-37-03.png "Update row")

22. Select the **Server name** and **Database name** previously specified, then from the drop-down select the name of the **Orders** table, and enter `OrderId` into the **Row id** field.

    ![In the Update row section, under Table name, Orders is selected.](media/2020-03-18-12-41-11.png "Update row section")

23. Press **Save**, then select the **Code View** button.

24. Add the following JSON within the `Update_row_(V2).inputs` object:

    ```json
    "body": {
        "OrderDate": "@{body('ContosoMakePDF')['OrderDate']}",
        "FirstName": "@{body('ContosoMakePDF')['FirstName']}",
        "LastName": "@{body('ContosoMakePDF')['LastName']}",
        "Address": "@{body('ContosoMakePDF')['Address']}",
        "City": "@{body('ContosoMakePDF')['City']}",
        "State": "@{body('ContosoMakePDF')['State']}",
        "PostalCode": "@{body('ContosoMakePDF')['PostalCode']}",
        "Country": "@{body('ContosoMakePDF')['Country']}",
        "Phone": "@{body('ContosoMakePDF')['Phone']}",
        "SMSOptIn": "@{body('ContosoMakePDF')['SMSOptIn']}",
        "SMSStatus": "@{body('ContosoMakePDF')['SMSStatus']}",
        "Email": "@{body('ContosoMakePDF')['Email']}",
        "ReceiptUrl": "@{body('ContosoMakePDF')['ReceiptUrl']}",
        "Total": "@{body('ContosoMakePDF')['Total']}",
        "PaymentTransactionId": "@{body('ContosoMakePDF')['PaymentTransactionId']}",
        "HasBeenShipped": "@{body('ContosoMakePDF')['HasBeenShipped']}"
    },
    ```

    After this has been added, the JSON will look as follows:

    ![JSON edits have been made.](media/2020-03-18-18-21-47.png "JSON edits have been made")

25. And modify the `path` variable for the `Update_row_(V2)` action to include the index key or OrderId as follows:

    ```json
    "path": "/v2/datasets/@{encodeURIComponent(encodeURIComponent('default'))},@{encodeURIComponent(encodeURIComponent('default'))}/tables/@{encodeURIComponent(encodeURIComponent('[dbo].[Orders]'))}/items/@{encodeURIComponent(encodeURIComponent(body('ContosoMakePDF')['OrderId']))}"
    ```

26. **Save** and return to the designer.

27. Your updated designer view should look like this:

    ![The Update row section displays the purchase fields.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image261.png "Update row section")

28. Finally, let us add one more step to remove the message from the queue. Press **+New Step**. Select **Service Bus**, then select the **Complete the message in a queue** action.

    ![In the Choose an action section, under Service Bus, the Complete the message in a queue is selected. ](media/2020-03-18-12-51-40.png "Choose an action section")

29. Select the **receiptgenerator** queue from the list.

30. Select **Lock token of the message** **\>** **Lock Token** from the list of outputs form the Trigger, and select **Save**.

    ![Lock token of the message field is set to the Lock Token of the Service Bus Trigger.](media/2020-03-18-12-54-28.png "Lock token is highlighted")

31. Select **Save**.

32. Select Run on the Logic App Designer, and then run the Contoso sports Web App and check out an Item.

33. Run the call center website app, and select the last Details link in the list.

    ![Screenshot of the Details link.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image264.png "Details link")

34. You should now see a Download receipt link because the database has been updated.

    ![In the Order Details window, the Download receipt link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image265.png "Order Details window")

35. Select the Download receipt link to see the receipt.

36. Return to the Logic app and you should see all green check marks for each step. If not, select the yellow status icon to find out details.

    ![In the Logic app, all steps have green checkmarks.](media/2020-03-18-19-05-39.png "Logic app")

### Task 3: Use Twilio to send SMS Order Notifications

#### Subtask 1: Configure your Twilio trial account

1. If you do not have a Twilio account, sign up for one for free at the following URL:

    [**https://www.twilio.com/try-twilio**](https://www.twilio.com/try-twilio)

    ![Screenshot of the Twilio account Sign up for free webpage.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image268.png "Twilio account Sign up webpage")

2. Select **All Products & Services**.

    ![In the Console, under Home, the All Products and Services (ellipses) button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image270.png "Console")

3. Select **Phone Numbers**.

    ![On the Console, under Numbers, Phone Numbers is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image271.png "Console")

4. Select **Get Started**.

    ![On the Console, under Phone Numbers, the Get Started button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image272.png "Console")

5. Select the **Get your first Twilio phone number** button.

    ![On the Get Started with Phone Numbers prompt, the Get your first Twilio phone number button displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image273.png "Get Started with Phone Numbers prompt")

6. Record the **Phone Number**, select the **Choose this Number** button on the **Your first Twilio Phone Number** prompt, and select **Done**.

    ![On the Your first Twilio Phone Number prompt, the number is obscured.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image274.png "Your first Twilio Phone Number prompt")

7. Select **Home**, then **Settings**. Authenticate if needed and then record the **Account SID** and **Auth Token** for use when configuring the Twilio Connector.

    ![On the Console, on the left, the Home button and the Settings menu tab are selected. On the right, under API Credentials, Account SID and Auth Token are circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image275.png "Console")

#### Subtask 2: Create a new logic app

1. Open **SQL Server Management Studio** and connect to the SQL Database for the **ContosoSportsDB** database.

    >**Note**: You can find the database server name by:
    > - Navigate the Azure ContosoSportsDB in the portal.
    > - In the Overview, locate the **Show database connection strings** link.
    > - Copy the **Server** parameter value.
    e.g. Server=tcp:``contososqlserver2019th.database.windows.net,1433``
    

    ![In Object Explorer, ContosoSportsDBserver1234.database is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image276.png "Object Explorer")

2. Under the **ContosoSportsDB** database, expand **Programmability**, right-click on **Stored Procedures**, select **New**, followed by **Stored Procedure...**

    ![In Object Explorer, the following path is expanded: ContosoSportsDBserver1234.database\\Databases\\ContosoSportsDB\\Programmability\\Stored Procedures. From the right-click menu for the Stored Procedures, New / Stored Procedure is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image277.png "Object Explorer")

3. Replace the Stored Procedure Template code with the following:

    ```sql
    CREATE PROCEDURE [dbo].[GetUnprocessedOrders]
    AS
    declare @returnCode int 
    SELECT @returnCode = COUNT(*) FROM [dbo].[Orders] WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null
    return @returnCode

    GO
    ```

4. Select **Execute** in the toolbar, or press the F5 key.

    ![Screenshot of the Execute button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image278.png "Execute button")

5. Delete the SQL script for the Stored Procedure from the code editor, and replace it with the following:

    ```sql
    CREATE PROCEDURE [dbo].[ProcessOrders]
    AS
    SELECT * FROM [dbo].[Orders] WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null;

    UPDATE [dbo].[Orders] SET SMSStatus = 'sent' WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null;
    ```

6. Select **Execute** in the toolbar, or press the F5 key.

    ![Screenshot of the Execute button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image278.png "Execute button")

7. In the Azure Management Portal, select the **+Create a resource** button, then **Web**, and, finally **Logic App**.

    ![In the Azure Portal, on the left side, the Create a resource menu option is selected. On the right, Web and Logic App are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image279.png "Azure Portal")

8. On the **Create logic app** blade, assign a value for **Name**, and set the Resource Group to **contososports**, then create the Logic App.

    ![In the Create logic app blade, the Name field is set to contososportssms. Under Resource group, Use existing is selected, and contososports is selected.](media/2020-03-19-11-31-05.png "Create logic app blade")

9. In the navigation menu to the left in the Portal, select **Resource Groups** then **contososports**, then the new Logic App you just created. 

10. In the Logic App blade, under the **DEVELOPMENT TOOLS** menu area, select **Logic App Designer**. Then, select the **Blank Logic App** Template.

    ![In the Logic Apps Designer, the Blank Logic App tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image282.png "Logic Apps Designer")

11. On the **Logic Apps Designer**, select **Schedule**. Then, select **Schedule - Recurrence**.

    ![In the Logic Apps Designer, the Schedule tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image283.png "Logic Apps Designer")

12. Set the **FREQUENCY** to **MINUTE**, and **INTERVAL** to 1.

    ![Under Recurrence, the Frequency field is Minute, and the Interval field is 1.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image284.png "Recurrence section")

13. Select the **+ New Step** button.

14. Type **SQL Server** into the filter box, and select the **SQL Server -- Execute stored procedure (V2)** action.

    ![Under Choose an action, sql server is typed in the search field. On the Actions tab, SQL Server (Execute stored procedure V2) is selected.](media/2020-03-19-11-34-57.png "Choose an action section")

15. Select the **Server name**, **Database name**, and `'[dbo].[GetUnprocessedOrders]` **Procedure name** values.

    ![In the Execute stored procedure section, the Procedure name is \[dbo\].\[GetUnprocessedOrders\].](media/2020-03-19-11-37-08.png "Execute stored procedure section")

16. Select **New Step**, and search for and select the **Control** object.

    ![The Control object is highlighted on the logic app designer pick tool.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image289.png "Buttons")

17. Select **New Step**, and search for and select the **Control -> Condition** object.

    ![The Control Condition object is highlighted on the logic app designer pick tool.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290b.png "Buttons")  

18. Select **Choose a value**, and then select **Return Code** from the Dynamic content tile.

    ![The Choose a value box and Return Code objects are highlighte in the Dynamic content tile in the Logic Designer.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290c.png "Buttons")

19. Specify **ReturnCode**, set the RELATIONSHIP to **is greater than**, and set the VALUE to **0**.

    ![Under Condition, Object Name is ReturnCode, Relationship is greater than, and Value is 0.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290.png "Condition section")

20. Select the **Add an action** link on the **If true** condition.

    ![Under If true, the Add an action button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image291.png "If yes section")

21. Select **SQL Server**, and then select the **SQL Server -- Execute stored procedure (V2)** action.

    ![Under If Yes, SQL Server - Execute stored procedure is circled.](media/2020-03-19-11-39-54.png "If yes section")

22. Select the **ProcessOrders** stored procedure in the Procedure name dropdown.

    ![Under If Yes, Execute stored procedure 2 is selected, and the Procedure name is \[dbo\].\[ProcessOrders\].](media/2020-03-19-11-40-49.png "If yes section")

23. Select the **Add an action** link.

    ![The Add an action button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image294.png "Add an action button")

24. Type **Twilio** in the filter box, and select the **Twilio -- Send Text Message (SMS)** connector.

    ![Under Show Microsoft managed APIs, the Search box is set to Twilio, and below, Twilio - Send Text Message (SMS) is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image295.png "Show Microsoft managed APIs")

25. Set the Connection Name to Twilio, specify your Twilio **Account SID** and **Authentication Token**, then select the **Create** button.

    ![In the Twilio - Send Text Message (SMS) section, fields are set to the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image296.png "Twilio - Send Text Message (SMS)")

26. Using the drop-down, select your Twilio number for the **FROM PHONE NUMBER** field. Specify a place holder phone number in the **TO PHONE NUMBER**, and a **TEXT** message.

    ![Under Send Text Message (SMS), the From Phone Number and To Phone Number fields are circled, and in the Text field is the message, Hello, your order has shipped!](media/2020-03-19-11-43-06.png "Send Text Message (SMS)")

27. On the Logic App toolbar, select the **Code View** button.

    ![The code view button is selected on the Logic App toolbar.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image298.png "Logic App toolbar")

28. Find the **Send\_Text\_Message\_(SMS)** action, and modify the body property of the Twilio action:

    ![The Code view displays the text message, and the from and to phone numbers.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image299.png "Code view")

    Add the following code between Hello and the comma:

    ```json
    "@{item()['FirstName']}"
    ```

    ![The Code view now displays the added code in the text message.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image300.png "Code view")

29. Modify the **to** property to pull the phone number from the item.

    ```json
    "to": "@{item()['Phone']}"
    ```

    ![The to phone number code now displays the updated line of code.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image301.png "Code view")

30. Immediately before the **Send\_Text\_Message\_(SMS)** section, create a new line, and add the following code:

  ```json
    "forEach_email": {
      "type": "Foreach",
      "foreach": "@body('Execute_stored_procedure_(V2)_2')['ResultSets']['Table1']",
      "actions": {
  ```

31. Remove the **runAfter** block from the **Send\_Text\_Message\_(SMS)** action.

    ![The runAfter block of code displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image302.png "Code view")

32. Locate the closing bracket of the **Send\_Text\_Message\_(SMS)** action, create a new line after it (be **SURE** to place a leading comma after the closing bracket), and add the following code:

  ```json
        },
        "runAfter": {
            "Execute_stored_procedure_(V2)_2": [
                "Succeeded"
            ]
        }
    }
  ```

33. Select **Save** on the toolbar to enable the logic app.

    ![On the Logic Apps Designer toolbar, the Save button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image304.png "Logic Apps Designer toolbar")

34. After the code for the **Send\_Text\_Message\_(SMS)** has been modified to be contained within the **forEach\_email** action and you save it, it should look like the following:

    ![The Code view displays the code from \"Foreach\" to \"Execute stored procedure.\"](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image303.png "Code view")

35. Your workflow should look like the image below, and you should receive a text for each order you placed.

    ![The Workflow diagram begins with Recurrence, then flows to Execute stored procedure, then to Condition. The Condition fields are as follows: Object Name, ReturnCode; Relationship, is greater than; Value, 0. Below the Workflow diagram is an If Yes box, with a workflow that begins wtih Execute stored procedure 2, and flows to forEach email. There is also an If No, Do Nothing box.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image305.png "Workflow diagram")

## After the hands-on lab

Duration: 10 minutes

### Task 1: Delete resources

1. Since the HOL is now complete, go ahead and delete all the Resource Groups that were created for this HOL. You will no longer need those resources and it will be beneficial to clean up your Azure Subscription.

You should follow all steps provided *after* attending the hands-on lab.
-->

## 演習 5: Azure Functions と Logic Apps でバックエンド処理を自動化する<a name="演習-5:-Azure-Functions-と-Logic-Apps-でバックエンド処理を自動化する"></a>

Contoso では、Azure Logic Apps と Azure Functions を使用して、注文処理時の PDF 形式の受領書生成とユーザー アラート生成処理を自動化したいと考えています。Logic Apps で C\# や node.js のカスタム スニペットを実行する場合、Azure Functions でカスタム関数を作成できます。[Azure Functions](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-overview) では Microsoft Azure のコンピューティング能力をサーバーレスで使用可能で、以下のようなタスクを実行する場合に便利です。

- Logic Apps で詳細な書式設定やフィールドの演算を行う。

- ワークフロー内での計算を実行する。

- C\# や node.js でサポートされている関数で Logic Apps の機能を拡張する。

### タスク 1: PDF 形式の受領書を生成する Azure 関数を作成する<a name="タスク-1:-PDF-形式の受領書を生成する-Azure-関数を作成する"></a>

1. Azure Portal 左上隅の [**+リソースの作成**] ボタンをクリックし、[**Compute**]、[**Function App**] の順に選択します。下部の [**作成**] ボタンをクリックします。

    ![Azure Portal 左側の [リソースの作成] ボタンが選択されている。中央では [新規] の下の [Compute] が選択されている。右側では [Compute] の [Function App] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image221.png "Azure Portal")

2. 以下の設定で新しい関数アプリをプロビジョニングし、デプロイします。

    - **リソース グループ**: 既存の **contososports** リソース グループを使用します。

    - **関数アプリ名**: _一意の名前を指定します。_

    - **発行**: コード

    - **ランタイム スタック**: .NET Core.

    - **リージョン**: このラボの eコマース Web アプリで使用されている場所と同じリージョンを選択します。

3. [**次へ: ホスティング>**] を選択します。

4. [**ホスティング**] タブで以下の値を選択し、[**確認および作成**] をクリックします。

    - **オペレーティング システム**: Windows

    - **プラン**: App Service プラン

    - **Windows プラン**: eコマース Web アプリで使用する App Service プランを選択します。

5. [**作成**] をクリックします。

6. **contososports** リソース グループのストレージ アカウントに移動し、[**アクセス キー**] を選択して、ストレージ アカウントの**接続文字列**をコピーします。後で使用するため、ストレージ アカウントの接続文字列をメモ帳に貼り付けます。

    ![ストレージ アカウントのリストが表示されている。  [アクセス キー] が指し示されている](media/2019-04-15-15-07-15.png "ストレージ アカウントのアクセス キー")

7. 作成した**関数アプリ**に移動し、[**構成**] を選択します。

    ![Contoso 関数アプリが表示されており、[構成] リンクが強調表示されている](media/2019-04-15-15-15-22.png "Contoso 関数アプリのアプリケーション設定")

8. **アプリケーション設定**を新規追加して以下の値を指定し、[**保存**] をクリックします。

    - **名前**: `contososportsstorage`.
    - **値**: ストレージ アカウントの接続文字列を入力

    ![関数アプリの更新されたアプリケーション設定。最新の値が表示されている](media/2019-04-15-16-18-36.png "関数アプリの更新されたアプリケーション設定")

9. Visual Studio ソリューション エクスプローラーを開き、**ContosoFunctionApp** プロジェクトを右クリックして [**発行**] をクリックし、関数アプリを発行します。

    ![Visual Studio ソリューション エクスプローラーが開かれている。Contoso 関数アプリのメニューが表示されている。関数アプリの発行が選択されている](media/2019-04-15-15-31-03.png "関数アプリの発行を選択")

10. [**発行先を選択**] ダイアログで [**既存のものを選択**]、[**プロファイルの作成**] の順に選択します。

11. **関数アプリ**を選択してから [**OK**] をクリックします。

    ![Azure 関数アプリ ツリーが表示されている。Contoso 関数アプリが選択されている](media/2019-04-15-15-34-54.png "Azure 関数アプリ ツリーの表示")

12. [**発行**] をクリックします。

    発行は 1 分程度で完了します。エラーが発生する可能性があるため、[**出力**] ウィンドウを確認します。

    ![ビルドの [出力] ウィンドウが表示されている。発行が成功したことを示すメッセージが表示されている](media/2019-04-15-15-33-20.png "[出力] ウィンドウ.")

13. Azure Portal で Contoso 関数アプリに戻り、新たに発行した関数アプリのテストを実行します。関数リストの中から、新しく作成された **ContosoMakePDF** 関数を選択します。

14. 右側のブレードの [**テスト**] リンクをクリックします。

    ![左側に関数アプリのリストが表示されている。ContosoMakePDF が選択されている。  右側のウィンドウの [テスト] リンクが矢印で指し示されている](media/2019-04-15-15-40-27.png "関数の [テスト] リンク")

15. HTTP メソッドから [**POST**] を選択します。

16. ラボ ファイルの Contoso.CreatePDFReport ディレクトリにある **sample.dat** ファイルを開きます。  内容を [**要求本文**] テキスト ボックスにコピーします。

    ![Windows エクスプローラーの一部のスクリーンショット。sample.dat ファイルのパスが示されている](media/2019-04-15-15-47-39.png "Sample.dat ファイル")

17. ブレード下部の [**実行**] ボタンをクリックします。

    ![[テスト] ブレードに sample.dat の内容が示されている。[要求本文] フィールドには JSON 形式の Order 文が示されている。[実行] ボタンが矢印で指し示されている](media/2019-04-15-15-52-59.png "[テスト] ブレードに sample.dat の内容が表示されている様子")

    > **注**: [Azure 関数] ブレード下部にも同様に [**実行**] ボタンがあります。どちらのボタンをクリックしても、同じように関数が実行されます。

    数秒後、以下の画像のようなログが表示されます。ステータス コード 200 が返されていれば成功です。  [**出力**] テキスト ボックスには Contoso の直近の購入データが出力されます。ファイルが作成され、Blob Storage に保存されたことを示すメッセージが表示されます。

    ![関数アプリのテスト結果のログのスクリーンショット。  右側のウィンドウにステータス コード 200 OK が表示されている](media/2019-04-15-15-58-54.png "関数アプリのテスト結果のログ")

18. ストレージ アカウント Blob に保存された PDF 形式の受領書を確認します。

    - ContosoSports のストレージ アカウントに移動します。
    - [**BLOB**] リンクを選択します。

    ![[設定] オプションが選択されている。[BLOB] リンクが矢印で指し示されている](media/2019-04-15-16-06-17.png "[BLOB] リンク")

19. 新たに作成された **receipts** Blob コンテナーを選択します。

    ![ストレージ アカウント Blob のリストが表示されている。receipts Blob コンテナーが強調表示されている](media/2019-04-15-16-08-35.png "[BLOB] リンクをクリック")

20. [**ContosoSportsLeague-Store-Receipt-XX.pdf**] リンクを開きます。

    ![新たに作成された PDF 形式の受領書のリストが表示されている様子を示すスクリーンショット。右側のウィンドウの [ダウンロード] リンクが矢印で指し示されている](media/2019-04-15-16-11-24.png "PDF 受領書")

    - `...` リンクを開き、ダウンロード メニュー アイテムを選択します。

    ![Contoso Sports League の PDF 受領書のサンプルが表示されている](media/2019-04-15-16-15-06.png "PDF 受領書のサンプル")

### タスク 2: 注文を処理する Azure Logic Apps を作成する<a name="タスク-2:-注文を処理する-Azure-Logic-Apps-を作成する"></a>

Azure Logic Apps でワークフローを作成して実行すると、コードを作成しないでもビジネス プロセスをより簡単にすばやく自動化できます。Logic Apps では、スケーラブルな統合やワークフローをクラウドで簡素化および実装できます。ビジュアル デザイナーを使用すると、ワークフローと呼ばれる一連の手順の処理をモデル化し、自動化できます。クラウドでもオンプレミスでも使用できる[コネクタが多数](https://docs.microsoft.com/ja-jp/azure/connectors/apis-list)用意されていて、サービスやプロトコルをすばやく統合できます。

Logic Apps を使用すると、以下のようなメリットがあります。

- 複雑なプロセスをわかりやすい設計ツールで設計できるため、時間を節約できる。

- コードでは実装が難しいパターンやワークフローをシームレスに実装できる。

- テンプレートを使用してすばやく導入できる。

- 独自のカスタム API、コード、アクションを使用してロジック アプリをカスタマイズできる。

- オンプレミスとクラウドで分断されたシステムを接続して同期できる。

- 最高レベルの統合をサポートする BizTalk サーバー、API 管理、Azure Functions、Azure Service Bus を構築できる。

1. ここからは、**receiptgenerator** キューにアイテムが追加されたときにトリガーとなるロジック アプリを作成します。Azure 管理ポータルで [**+リソースの作成**] ボタンをクリックし、「**Logic App**」を検索します。次にその検索結果を選択し、[**作成**] をクリックします。

    ![Azure Portal の [Marketplace] で [すべて] が選択されている。[すべて] の検索フィールドに「Logic App」と入力されている。[名前] の下の「Logic App」が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image236.png "Azure Portal")

2. サブスクリプション名に合わせて **ContosoLogicApplication** と命名します。リソース グループは既存の **contososports** を使用します。Web アプリとストレージ アカウントで**同一リージョン**を選択します。[**作成**] をクリックします。

    ![[ロジック アプリの作成] ブレードの [名前] フィールドで ContosoLogicApplication が選択されている。[リソース グループ] で [既存のものを使用] ラジオ ボタンが選択されている。名前は contososports](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image237.png "[ロジック アプリの作成] ブレード")

3. デプロイが完了したら、[**すべてのサービス**] を選択してロジック アプリを開きます。「**Logic App**」を検索して選択し、先ほど作成したロジック アプリを選択します。

    ![Azure Portal の検索フィールドに「logic」と入力されており、その下で Logic apps が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image238.png "Azure Portal")

4. [**ロジック アプリ デザイナー**] リンクを選択します。

    ![[Logic app] ブレードの [開発ツール] で [ロジック アプリ デザイナー] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image239.png "[Logic app] ブレード")

5. ロジック アプリ デザイナーの [**テンプレート**] で [**空のロジック アプリ**] を選択します。

    ![ロジック アプリ デザイナーで [空のロジック アプリ] が選択されている](media/2019-03-29-12-56-10.png "ロジック アプリ デザイナー")

6. [**すべて**] タブ、[**Azure キュー**] の順に選択します。

    ![[サービス] セクションで [Azure Service Bus] タイルが選択されている](media/2020-03-18-12-12-10.png "[サービス] セクション")

7. [**Service Bus - キューにメッセージが届く (オートコンプリート)**] の順に選択します。

    ![[すべてのトリガーを検索] セクションの [Service Bus - キューにメッセージが届く (オートコンプリート)]](media/2020-03-18-12-13-24.png "[すべてのトリガーを検索] セクション")
    ![]()

8. 接続名として「**ContosoQueue**」を指定し、リストから Contoso のストレージ アカウントを選択して [**作成**] をクリックします。

    ![[キューにメッセージが届く] で ContosoQueue という接続名が指定されている。[Service Bus 名前空間] で contosooiyxeonvhew7u が選択されている](media/2020-03-18-12-15-23.png "[キューにメッセージが届く]")

9. [Service Bus ポリシー] リストから **RootManageSharedAccessKey*** を選択し、[**作成**] をクリックします。

    ![RootManageSharedAccessKey が選択されている](media/2020-03-18-12-17-17.png "RootManageSharedAccessKey が選択されている")

10. ドロップダウン メニューで **receiptgenerator** キューを選択し、[**新しい手順**]、[**アクションの追加**] の順にクリックします。

    ![[キューにメッセージが届く] で [キュー名] に「receiptgenerator」が指定されている](media/2020-03-18-12-19-06.png "キュー名")

    >**注**: 必要に応じて [**間隔**] と [**頻度**] を設定し、既定より短い 30 秒間隔などで新規アイテムを確認することもできます。この方法を使用すると、ラボの後の手順で、Service Bus キューに新しいメッセージが送信されてからロジック アプリがトリガーされるまでの遅延を短縮できます。

11. [**+ 新しい手順**] ボタン、[**Azure Functions**] の順に選択します。

    ![[アクションの選択] セクションの [サービス] で [Azure Functions] タイルが選択されている](media/2020-03-18-12-21-44.png "[アクションの選択]")

12. 先ほど作成した **Azure 関数アプリ**を選択します。

    ![[Azure 関数] の [アクション] タブで Azure 関数アプリの ContosoFunctionApp というアクションが 1 つリストに掲載されている](media/2020-03-18-12-22-46.png "Azure 関数")

13. Azure 関数の **ContosoMakePDF** を選択します。

    ![[Azure 関数] の [アクション] タブで Azure 関数の ContosoMakePDF というアクションが 1 つリストに掲載されている](media/2020-03-18-12-23-39.png "Azure 関数")

14. 要求本文に以下のコードを追加します。

    ```json
    {"Order": pick Content from list }
    ```

    必ず JSON 形式の文法に従います。誤ってコードの行末に「:」が付けられることがありますが、左側に付けます。以下に例を示します。

    ![ContosoMakePDF で上記の JSON コードが要求本文に追加され、その右には、前の手順から挿入するパラメーターとして Content が選択されている](media/2020-03-18-12-25-29.png "ContosoMakePDF")

15. [**保存**] をクリックしてロジック アプリを保存します。

16. ロジック アプリを実行します。前の手順で PDF 生成テスト用に送信した注文が処理されます。Azure Storage Explorer や Visual Studio Cloud Explorer でストレージ アカウントに移動して receipts コンテナーを開くと、作成された PDF を表示できます。

    ![Azure Storage Explorer の左側にツリー ビューが展開されている (ストレージ アカウント\\contososportsstorage01r\\Blob コンテナー)。Blob コンテナーで receipts が選択されている。右側では ContosoSportsLeague-Store-Receipt-72.pdf が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image252.png "Azure Storage Explorer")

17. ダブルクリックすると購入受領書が表示されます。

18. ロジック アプリ デザイナー画面で [**デザイナー**] ボタンを選択し、データベース更新と処理済みメッセージをキューから削除する処理の 2 つの手順をフローに追加します。デザイナーに戻って [**+ 新しい手順**] を選択します。

    ![デザイナーの [新しい手順] リンクが囲まれている。[新しい手順] の [アクションの追加] タイルが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image254.png "デザイナー")

19. [**SQL Server**] を選択します。

    ![[サービス] セクションで [SQL Server] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image255.png "[サービス] セクション")

20. [**SQL Server - 行の更新 (V2)**] を選択します。

    ![[SQL Server] セクションの [アクション] タブで [SQL Server - 行の更新 (V2)] が選択されている](media/2020-03-18-12-35-07.png "[SQL Server] セクション")

21. 以下の値を入力し、[**作成**] をクリックします。

    - 認証の種類: **SQL Server Authentication**

    - SQL Server 名: 前の手順でコピーした SQL Database フェールオーバー クラスターの読み取り/書き込みリスナー エンドポイントの DNS 名を入力

    - SQL Database 名: `ContosoSportsDB`

    - ユーザー名: `demouser`

    - パスワード: `demo@pass123`

    ![前の手順で定義された設定が [行の更新] セクションに表示されている](media/2020-03-18-12-37-03.png "行の更新")

22. [**サーバー名**] と [**データベース名**] で前の手順で指定した名前を選択し、ドロップダウン リストで **Orders** テーブルを選択し、[**行 ID**] フィールドに `OrderId` という名前を入力します。

    ![[行の更新] セクションの [テーブル名] で Orders が指定されている](media/2020-03-18-12-41-11.png "[行の更新] セクション")

23. [**保存**]、[**コード ビュー**] ボタンの順にクリックします。

24. `Update_row_(V2).inputs` オブジェクトに以下の JSON コードを追加します。

    ```json
    "body": {
        "OrderDate": "@{body('ContosoMakePDF')['OrderDate']}",
        "FirstName": "@{body('ContosoMakePDF')['FirstName']}",
        "LastName": "@{body('ContosoMakePDF')['LastName']}",
        "Address": "@{body('ContosoMakePDF')['Address']}",
        "City": "@{body('ContosoMakePDF')['City']}",
        "State": "@{body('ContosoMakePDF')['State']}",
        "PostalCode": "@{body('ContosoMakePDF')['PostalCode']}",
        "Country": "@{body('ContosoMakePDF')['Country']}",
        "Phone": "@{body('ContosoMakePDF')['Phone']}",
        "SMSOptIn": "@{body('ContosoMakePDF')['SMSOptIn']}",
        "SMSStatus": "@{body('ContosoMakePDF')['SMSStatus']}",
        "Email": "@{body('ContosoMakePDF')['Email']}",
        "ReceiptUrl": "@{body('ContosoMakePDF')['ReceiptUrl']}",
        "Total": "@{body('ContosoMakePDF')['Total']}",
        "PaymentTransactionId": "@{body('ContosoMakePDF')['PaymentTransactionId']}",
        "HasBeenShipped": "@{body('ContosoMakePDF')['HasBeenShipped']}"
    },
    ```

    追加後の JSON コードは以下のようになります。

    ![編集済みの JSON コード](media/2020-03-18-18-21-47.png "編集済みの JSON コード")

25. `Update_row_(V2)` アクションの `path` 変数を変更し、以下のようにインデックス キーまたは OrderId を追加します。

    ```json
    "path": "/v2/datasets/@{encodeURIComponent(encodeURIComponent('default'))},@{encodeURIComponent(encodeURIComponent('default'))}/tables/@{encodeURIComponent(encodeURIComponent('[dbo].[Orders]'))}/items/@{encodeURIComponent(encodeURIComponent(body('ContosoMakePDF')['OrderId']))}"
    ```

26. [**保存**] をクリックしてからデザイナーに戻ります。

27. 更新後のデザイナー ビューは以下のようになります。

    ![[行の更新] セクションに購入フィールドが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image261.png "[行の更新] セクション")

28. 最後に、キューからメッセージを削除する手順を追加します。[**+新しい手順**] をクリックします。[**Service Bus**]、 [**キュー内のメッセージを完了**] アクションの順に選択します。

    ![[Service Bus] の [アクションの選択] セクションで [キュー内のメッセージを完了] が選択されている](media/2020-03-18-12-51-40.png "[アクションの選択] セクション")

29. リストから **receiptgenerator** キューを選択します。

30. トリガーの出力フォーム リストから [**メッセージのロック トークン**]、[**ロック トークン**] の順に選択し、[**保存**] をクリックします。

    ![[メッセージのロック トークン] フィールドで Service Bus のトリガーに [ロック トークン] が選択されている](media/2020-03-18-12-54-28.png "[ロック トークン] が強調表示されている")

31. [**保存**] をクリックします。

32. [ロジック アプリ デザイナーで実行] を選択してから Contoso Sports Web アプリを選択し、アイテムを確認します。

33. コール センター Web サイト アプリを実行し、リスト末尾の [詳細] リンクを選択します。
    ![[詳細] リンクのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image264.png "[詳細] リンク")

34. データベースが更新されたため、[受領書のダウンロード] リンクが表示されます。

    ![[注文の詳細] ウィンドウで [受領書のダウンロード] リンクが囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image265.png "[注文の詳細] ウィンドウ")

35. [受領書のダウンロード] リンクを選択して受領書を表示します。

36. ロジック アプリに戻って、すべての手順に緑色のチェック マークが付いていることを確認します。黄色の状態アイコンがある場合は、選択して詳細を確認します。

    ![ロジック アプリのすべての手順に緑色のチェック マークが付いている](media/2020-03-18-19-05-39.png "ロジック アプリ")

### タスク 3: Twilio を使用して SMS で注文通知を送信する<a name="タスク-3:-Twilio-を使用して-SMS-で注文通知を送信する"></a>

#### サブタスク 1: Twilio の試用アカウントを構成する<a name="サブタスク-1:-Twilio-の試用アカウントを構成する"></a>

1. Twilio アカウントを所有していない場合は、次の URL から無料アカウントにサインアップします。

    [**https://www.twilio.com/try-twilio**](https://www.twilio.com/try-twilio)

    ![Twilio の無料アカウントのサインアップ Web ページのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image268.png "Twilio アカウントのサインアップ Web ページ")

2. [**All Products & Services**] を選択します。

    ![コンソールの [Home] で [All Products and Services (ellipses)] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image270.png "コンソール")

3. [**Phone Numbers**] を選択します。

    ![コンソールの [Numbers] で [Phone Numbers] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image271.png "コンソール")

4. [**Get Started**] を選択します。

    ![コンソールの [Phone Numbers] で [Get Started] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image272.png "コンソール")

5. [**Get your first Twilio phone number**] ボタンを選択します。

    ![[Get Started with Phone Numbers] プロンプトで [Get your first Twilio phone number] ボタンが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image273.png "[Get Started with Phone Numbers] プロンプト")

6. [**Phone Number**] をメモしておき、[**Your first Twilio Phone Number**] プロンプトで [**Choose this Number**] ボタンを選択し、[**Done**] をクリックします。

    ![[Your first Twilio Phone Number] プロンプトで電話番号がぼかして表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image274.png "[Your first Twilio Phone Number] プロンプト")

7. [**Home**]、[**Settings**] の順に選択します。必要に応じて認証を受け、後で Twilio Connector を構成するときに使用するため [**Account SID**] と [**Auth Token**] をメモしておきます。

    ![コンソール左側の [Home] ボタンと [Settings] メニュー タブが選択されている。右側の [API Credentials] で [Account SID] と [Auth Token] が囲まれている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image275.png "コンソール")

#### サブタスク 2: 新しいロジック アプリを作成する<a name="サブタスク-2:-新しいロジック-アプリを作成する"></a>

1. **SQL Server Management Studio** を開き、**ContosoSportsDB** データベースとして使用する SQL Database に接続します。

    >**注**: データベース サーバー名は以下の手順で検索します。
    > - Azure Portal で ContosoSportsDB に移動します。
    > - [概要] で [**データベース接続文字列の表示**] リンクを検索します。
    > - **Server** パラメーターの値をコピーします。
    例: Server=tcp:``contososqlserver2019th.database.windows.net,1433``

    ![オブジェクト エクスプローラーで ContosoSportsDBserver1234.database が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image276.png "オブジェクト エクスプローラー")

2. **ContosoSportsDB** データベースで [**プログラマビリティ**] を展開し、[**ストアド プロシージャ**] を右クリックしてから [**新規**]、[**ストアド プロシージャ...**] の順に選択します。

    ![オブジェクト エクスプローラーで ContosoSportsDBserver1234.database\\データベース\\ContosoSportsDB\\プログラマビリティ\\ストアド プロシージャの順に選択されている。[ストアド プロシージャ] の右クリック メニューで [新規]、[ストアド プロシージャ] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image277.png "オブジェクト エクスプローラー")

3. ストアド プロシージャ テンプレートのコードを以下のように変更します。

    ```sql
    CREATE PROCEDURE [dbo].[GetUnprocessedOrders]
    AS
    declare @returnCode int 
    SELECT @returnCode = COUNT(*) FROM [dbo].[Orders] WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null
    return @returnCode

    GO
    ```

4. ツールバーで [**実行**] をクリックするか F5 キーを押します。

    ![[実行] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image278.png "[実行] ボタン")

5. コード エディターでストアド プロシージャの SQL スクリプトを削除し、以下のように変更します。

    ```sql
    CREATE PROCEDURE [dbo].[ProcessOrders]
    AS
    SELECT * FROM [dbo].[Orders] WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null;

    UPDATE [dbo].[Orders] SET SMSStatus = 'sent' WHERE PaymentTransactionId is not null AND PaymentTransactionId <> '' AND Phone is not null AND Phone <> '' AND SMSOptIn = '1' AND SMSStatus is null;
    ```

6. ツールバーで [**実行**] をクリックするか F5 キーを押します。

    ![[実行] ボタンのスクリーンショット](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image278.png "[実行] ボタン")

7. Azure 管理ポータルで [**+リソースの作成**] ボタン、[**Web**]、[**ロジック アプリ**] の順に選択します。

    ![Azure Portal 左側の [リソースの作成] メニュー オプションが選択されている。右側では [Web] と [ロジック アプリ] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image279.png "Azure Portal")

8. [**ロジック アプリの作成**] ブレードで [**名前**] の値を割り当て、リソース グループを **contososports** と指定し、ロジック アプリを作成します。

    ![[ロジック アプリの作成] ブレードの [名前] フィールドが contososportssms に設定されている。[リソース グループ] で [既存のものを使用]、contososports が選択されている](media/2020-03-19-11-31-05.png "[ロジック アプリの作成] ブレード")

9. Azure Portal 左側のナビゲーション メニューで [**リソース グループ**] を選択してから **contososports**、先ほど作成した新しいロジック アプリの順に選択します。 

10. [ロジック アプリ] ブレードの [**開発ツール**] メニューで [**ロジック アプリ デザイナー**] を選択します。次に、[**空のロジック アプリ**] テンプレートを選択します。

    ![ロジック アプリ デザイナーで [空のロジック アプリ] タイルが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image282.png "ロジック アプリ デザイナー")

11. **ロジック アプリ デザイナー**で [**スケジュール**] を選択します。次に、[**スケジュール - 繰り返し**] を選択します。

    ![ロジック アプリ デザイナーで [スケジュール] タイルが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image283.png "ロジック アプリ デザイナー")

12. [**頻度**] を [**分**] に設定し、[**間隔**] を 1 に設定します。

    ![[繰り返し] の [頻度] フィールドが [分]、[間隔] フィールドが 1 に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image284.png "[繰り返し] セクション")

13. [**+ 新しい手順**] ボタンを選択します。

14. 検索ボックスに「**SQL Server**」と入力し、[**SQL Server - ストアド プロシージャの実行(V2)**] アクションを選択します。

    ![[アクションの選択] セクションの検索フィールドに「SQL Server」と入力されている。[アクション] タブで [SQL Server - ストアド プロシージャの実行(V2)] が選択されている](media/2020-03-19-11-34-57.png "[アクションの選択] セクション")

15. [**サーバー名**]、[**データベース名**]、[**プロシージャ名**] (`'[dbo].[GetUnprocessedOrders]`) の値を指定します。

    ![[ストアド プロシージャの実行] セクションで [プロシージャ名] が \[dbo\].\[GetUnprocessedOrders\] に指定されている](media/2020-03-19-11-37-08.png "[ストアド プロシージャの実行] セクション")

16. [**新しい手順**] を選択し、**コントロール** オブジェクトを検索して選択します。

    ![ロジック アプリ デザイナーでコントロール オブジェクトが強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image289.png "ボタン")

17. [**新しい手順**] を選択し、[**コントロール - 条件**] オブジェクトを検索して選択します。

    ![ロジック アプリ デザイナーで [コントロール - 条件] オブジェクトが強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290b.png "ボタン")  

18. [**値の選択**] を選択し、[動的コンテンツ] タイルで **ReturnCode** を選択します。

    ![ロジック アプリ デザイナーの [動的コンテンツ] タイルで [値の選択] ボックス、ReturnCode オブジェクトが強調表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290c.png "ボタン")

19. **ReturnCode** を指定し、関係を [**より大きい**]、値を **0** に設定します。

    ![[条件] でオブジェクト名が ReturnCode、関係が [より大きい]、値が 0 に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image290.png "[条件] セクション")

20. [**true の場合**] という条件で [**アクションの追加**] リンクを選択します。

    ![[true の場合] で [アクションの追加] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image291.png "[true の場合] セクション")

21. [**SQL Server**]、[**SQL Server - ストアド プロシージャの実行 (V2)**] アクションの順に選択します。

    ![[true の場合] で [SQL Server - ストアド プロシージャの実行 (V2)] が囲まれている](media/2020-03-19-11-39-54.png "[true の場合] セクション")

22. [プロシージャ名] ドロップダウン リストで **ProcessOrders** ストアド プロシージャを選択します。

    ![[true の場合] で [ストアド プロシージャの実行 (V2)] が選択されていて、プロシージャ名に \[dbo\].\[ProcessOrders\] が指定されている](media/2020-03-19-11-40-49.png "[true の場合] セクション")

23. [**アクションの追加**] リンクをクリックします。

    ![[アクションの追加] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image294.png "[アクションの追加] ボタン")

24. 検索ボックスに「**Twilio**」と入力し、[**Twilio - テキスト メッセージを送信 (SMS)**] コネクタを選択します。

    ![[Microsoft が管理している API を表示] の検索ボックスに「Twilio」と入力されていて、その下で [Twilio - テキスト メッセージを送信 (SMS)] が選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image295.png "Microsoft が管理している API を表示")

25. [接続名] を Twilio に設定し、Twilio の**アカウント SID** と**認証トークン**を指定してから [**作成**] ボタンをクリックします。

    ![[Twilio - テキスト メッセージを送信 (SMS)] セクションのフィールドが前の手順で定義した値に設定されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image296.png "Twilio - テキスト メッセージを送信 (SMS)")

26. [**発信元電話番号**] フィールドで、Twilio で使用する電話番号をドロップダウン メニューから選択します。[**発信先電話番号**] の電話番号と [**テキスト**] メッセージの値を指定します。

    ![[テキスト メッセージを送信 (SMS)] の [発信元電話番号] と [発信先電話番号] が囲まれている。[テキスト] フィールドには「Hello, your order has shipped!」というメッセージが入力されている](media/2020-03-19-11-43-06.png "テキスト メッセージを送信 (SMS)")

27. ロジック アプリのツールバーで [**コード ビュー**] ボタンを選択します。

    ![ロジック アプリのツールバーで [コード ビュー] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image298.png "ロジック アプリのツールバー")

28. **Send\_Text\_Message\_(SMS)** アクションを検索し、Twilio アクション本文のプロパティを以下のように変更します。

    ![コード ビューにテキスト メッセージ、発信元電話番号、発信先電話番号が表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image299.png "コード ビュー")

    「Hello」とその後のコンマの間に以下のコードを追加します。

    ```json
    "@{item()['FirstName']}"
    ```

    ![コード ビューのテキスト メッセージにコードが追加されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image300.png "コード ビュー")

29. **to** プロパティにアイテムから電話番号をプルします。

    ```json
    "to": "@{item()['Phone']}"
    ```

    ![コード行が更新され、電話番号のコードが追加されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image301.png "コード ビュー")

30. **Send\_Text\_Message\_(SMS)** セクションの直前に新規行を挿入し、以下のコードを追加します。

  ```json
    "forEach_email": {
      "type": "Foreach",
      "foreach": "@body('Execute_stored_procedure_(V2)_2')['ResultSets']['Table1']",
      "actions": {
  ```

31. **Send\_Text\_Message\_(SMS)** アクションの **runAfter** ブロックを削除します。

    ![runAfter ブロックのコードが表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image302.png "コード ビュー")

32. **Send\_Text\_Message\_(SMS)** アクションの閉じかっこの直後に新規行を挿入し (**必ず**閉じかっこの直後にコンマを挿入します)、以下のコードを追加します。

  ```json
        },
        "runAfter": {
            "Execute_stored_procedure_(V2)_2": [
                "Succeeded"
            ]
        }
    }
  ```

33. ツールバーで [**保存**] をクリックし、ロジック アプリを有効化します。

    ![ロジック アプリ デザイナー ツールバーで [保存] ボタンが選択されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image304.png "ロジック アプリ デザイナー ツールバー")

34. 以下のように、**forEach\_email** アクションに **Send\_Text\_Message\_(SMS)** 部分が含まれるように変更し、コードを保存します。

    ![\"forEach\" から \"Execute_stored_procedure\" までのコードがコード ビューで表示されている](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image303.png "コード ビュー")

35. 以下のワークフローに従って、注文が確定するとテキスト メッセージが送信されます。

    ![[繰り返し]、[ストアド プロシージャの実行]、[条件] と続くワークフロー図。[条件] フィールドの内容はオブジェクト名、ReturnCode、関係 = より大きい、値 = 0。ワークフロー図下段の [true の場合] は [ストアド プロシージャの実行 2]、[forEach_email] と続く。[false の場合] には何もない](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image305.png "ワークフロー図")

## ハンズオン ラボ終了後の作業<a name="ハンズオン-ラボ終了後の作業"></a>

時間: 10 分

### タスク 1: リソースを削除する<a name="タスク-1:-リソースを削除する"></a>


1. 以上でハンズオン ラボは終了です。次へ進み、ラボで作成したリソース グループをすべて削除します。これらのリソースはもう不要です。Azure サブスクリプションを整理するためにも、削除することをおすすめします。

ハンズオン ラボ*修了後*、すべての手順を復習してください。
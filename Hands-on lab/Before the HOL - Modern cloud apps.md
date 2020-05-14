<!--
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Modern cloud apps
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
March 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.# Modern Cloud Apps setup

**Contents**
-->
<!-- TOC -->
<!--
- [Modern cloud apps before the hands-on lab setup guide](#Modern-cloud-apps-before-the-hands-on-lab-setup-guide)
  - [Requirements](#Requirements)
  - [Before the hands-on lab](#Before-the-hands-on-lab)
    - [Task 1: Download GitHub resources](#Task-1-Download-GitHub-resources)
    - [Task 2: Deploy Lab VM Resources to Azure](#Task-2-Deploy-Lab-VM-Resources-to-Azure)
    - [Task 3: Deploy Environment Resources to Azure](#Task-3-Deploy-Environment-Resources-to-Azure)
    - [Task 4: Explore the Contoso Sports League sample](#Task-4-Explore-the-Contoso-Sports-League-sample)
-->
<!-- /TOC -->
<!--
# Modern cloud apps before the hands-on lab setup guide

## Requirements

- Microsoft Azure MSDN subscription

  - You will need permissions within the Azure Subscription and Azure Active Directory (Azure AD) to create users and setup Azure AD B2C.

- Local machine or Azure virtual machine configured with:

  - Visual Studio 2019 Community Edition or later
  - Windows Server 2016

## Before the hands-on lab

Duration: 30 minutes

Before initiating the hands-on lab, you will setup an environment to use for the rest of the exercises.

### Task 1: Download GitHub resources

1. Open a browser window to the Cloud Workshop GitHub repository (<https://github.com/microsoft/MCW-Modern-cloud-apps>).

2. Select **Clone or download**, then select **Download Zip**.

    ![Download Zip from Github repository.](images/Setup/2019-06-24-17-08-18.png)

3. Extract the zip file to your local machine, be sure to keep note of where you have extracted the files. You should now see a set of folders:

    ![Windows Explorer showing the extracted files.](images/Setup/2019-06-24-17-10-56.png)

### Task 2: Deploy Lab VM Resources to Azure

1. Select the following **Deploy to Azure** button to deploy the ARM Template with the Lab VM resources for this lab. This link will deep link into the Azure Portal, passing in the ARM Template for deploying the resources for this lab.

    [![Deploy to Azure button.](images/azure-deploy-button-small.png "Deploy to Azure")](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FMCW-Modern-cloud-apps%2Fmaster%2FHands-on%20lab%2Fscripts%2Flabvm%2Ftemplate.json)

    >**Note**: If you have issues with the **Deploy to Azure** link, then do a new **Custom deployment** in the Azure Portal using the `/Hands-on lab/scripts/labvm/template.json` ARM Template within the lab files.

2. On the **Custom deployment** blade, select **Create new** for the **Resource group** field, and enter `ContosoSports-[your initials or first name]`.

3. Select **Edit parameters**.

    ![Select Edit Parameters.](images/Setup/2019-06-24-17-17-05.png)

4. On the **Edit parameters** pane, select the **Load file** button.

5. Locate and open the `\Hands-on lab\Scripts\labvm\parameters.json` file within the extracted files.

6. Select **Save**.

7. Check the **I agree to the terms and conditions stated above** checkbox.

8. Select **Purchase**.

    ![Select Purchase.](images/Setup/2019-06-24-17-20-12.png)

9. The deployment will take 15-30 minutes to complete. Continue to the next Task while this is deploying.

    To view the progress, select the **Deployments** link, then select the **Microsoft.Template** deployment.

    ![View template deployment status.](images/Setup/2019-06-24-17-22-19.png "Resource group deployments")

    > **Note**: A configuration script to install SSMS and the requires lab files will run after the deployment of the LabVM completes. The task will be listed on the deployment progress screen as `LabVM/CustomScriptExtension`. You should wait for this task to complete before attempting to log into the LabVM in the next task, as it downloads and installs files you will need.
    >
    > ![The CustomScriptExtension task in highlighted in the list of deployment tasks.](media/deployment-progress.png "Deployment progress")

### Task 3: Deploy Environment Resources to Azure

1. Select the following **Deploy to Azure** button to deploy the ARM Template with the Environment resources for this lab. This link will deep link into the Azure Portal, passing in the ARM Template for deploying the resources for this lab.

    [![Deploy to Azure button.](images/azure-deploy-button-small.png "Deploy to Azure")](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FMCW-Modern-cloud-apps%2Fmaster%2FHands-on%20lab%2Fscripts%2Fenvironment%2Ftemplate.json)

    >**Note**: If you have issues with the **Deploy to Azure** link, then do a new **Custom deployment** in the Azure Portal using the `/Hands-on lab/scripts/environment/template.json` ARM Template within the lab files.

2. On the **Custom deployment** blade, select **Create new** for the **Resource group** field, and enter `contososports[your initials or first name]`.

3. Select **Edit parameters**.

    ![Select Edit Parameters.](images/Setup/2019-06-24-17-17-05.png)

4. On the **Edit parameters** pane, select the **Load file** button.

5. Locate and open the `\Hands-on lab\Scripts\environment\parameters.json` file within the extracted files.

6. Select **Save**.

7. On the **Location** field for the Custom deployment, choose the Azure Region closest to you.

    > **Note**: For this lab, it is recommended you use the **East US**, **North Europe**, or **Australia East** Azure Region. There are certain Azure regions that don't support all the resources provisioned by the ARM Template. This limitation can also vary depending on restrictions applied to the type of Azure Subscription you are using.

7. Check the **I agree to the terms and conditions stated above** checkbox.

8. Select **Purchase**.

    ![The I agreed to the terms and conditions state box is checked, then select Purchase.](images/Setup/2019-06-24-17-20-12.png)

9. The deployment will take 5 - 10 minutes to complete.

### Task 4: Explore the Contoso Sports League sample

1. Connect to the **LabVM** that was deployed using the previous template using Remote Desktop, using these credentials:

    - **Admin username**: `demouser`
    - **Admin password**: `demo@pass123`


    > **Note**: Be sure to wait until the **Lab VM** ARM Template deployment has completed before connecting to the **LabVM** virtual machine.

2. Open the `C:\MCW` folder.

3. From the **Contoso Sports League** folder under **MCW**, open the Visual Studio Solution file: `Contoso.Apps.SportsLeague.sln`.

4. The solution contains the following projects:

    | Project | Description |
    |:----------|:-------------|
    | Contoso.Apps.SportsLeague.Web |   Contoso Sports League e-commerce application |
    | Contoso.Apps.SportsLeague.Admin |   Contoso Sports League call center admin application |
    | Contoso.Apps.Common  |   Shared tier |
    | Contoso.Apps.SportsLeague.Data  |   Shared tier |
    | Contoso.Apps.FunctionApp  |   Function app tier |
    | Contoso.Apps.SportsLeague.Offers |  API for returning list of available products |
    | Contoso.Apps.PaymentGateway   |     API for payment processing |

You should follow all the steps provided *before* performing the Hands-on lab.
-->

![Microsoft Cloud Workshop](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshop")

<div class="MCWHeader1">
最新のクラウド アプリ
</div>

<div class="MCWHeader2">
ハンズオン ラボ事前セットアップ ガイド
</div>

<div class="MCWHeader3">
2020 年 3 月
</div>

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。著作権法による制限に関係なく、マイクロソフトの書面による許可なしに、このドキュメントの一部または全部を複製したり、検索システムに保存または登録したり、別の形式に変換したりすることは、手段、目的を問わず禁じられています。ここでいう手段とは、複写や記録など、電子的、または物理的なすべての手段を含みます。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

© 2020 Microsoft Corporation. All rights reserved.

Microsoft および <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> (英語) に掲載されているその他の商標は、マイクロソフト グループ各社の商標です。その他すべての商標は、その所有者に帰属します。最新のクラウド アプリのセットアップ

**目次**

<!-- TOC -->

- [最新のクラウド アプリ ハンズオン ラボ事前セットアップ ガイド](#最新のクラウド-アプリ-ハンズオン-ラボ事前セットアップ-ガイド)
  - [要件](#要件)
  - [ハンズオン ラボの事前準備](#ハンズオン-ラボの事前準備)
    - [タスク 1: GitHub のリソースをダウンロードする](#タスク-1:-GitHub-のリソースをダウンロードする)
    - [タスク 2: ラボ VM のリソースを Azure にデプロイする](#タスク-2:-ラボ-VM-のリソースを-Azure-にデプロイする)
    - [タスク 3: 環境のリソースを Azure にデプロイする](#タスク-3:-環境のリソースを-Azure-にデプロイする)
    - [タスク 4: Contoso Sports League のサンプルを確認する](#タスク-4:-Contoso-Sports-League-のサンプルを確認する)

<!-- /TOC -->

# 最新のクラウド アプリ ハンズオン ラボ事前セットアップ ガイド<a name="最新のクラウド-アプリ-ハンズオン-ラボ事前セットアップ-ガイド"></a>

## 要件<a name="要件"></a>

- Microsoft Azure MSDN サブスクリプション

  - ユーザー作成と Azure AD B2C のセットアップに必要な Azure サブスクリプションと Azure Active Directory (Azure AD) のアクセス許可が必要です。

- 以下が構成されたローカル マシンまたは Azure 仮想マシン

  - Visual Studio 2019 Community Edition またはそれ以降
  - Windows Server 2016

## ハンズオン ラボの事前準備<a name="ハンズオン-ラボの事前準備"></a>

時間: 30 分

ハンズオン ラボを開始する前に、ラボで使用する環境をセットアップします。

### タスク 1: GitHub のリソースをダウンロードする<a name="タスク-1:-GitHub-のリソースをダウンロードする"></a>

1. ブラウザーのウィンドウを開いて Cloud Workshop の GitHub リポジトリ (<https://github.com/microsoft/MCW-Modern-cloud-apps>、英語) にアクセスします。

2. [**Clone or download**]、[**Download Zip**] の順に選択します。

    ![Github リポジトリから　Zip をダウンロードする](images/Setup/2019-06-24-17-08-18.png)

3. Zip ファイルをローカル マシンに展開します。ファイルを展開した場所はメモしておいてください。展開されるフォルダーは以下のとおりです。

    ![展開されたファイルを Windows エクスプローラーで表示](images/Setup/2019-06-24-17-10-56.png)

### タスク 2: ラボ VM のリソースを Azure にデプロイする<a name="タスク-2:-ラボ-VM-のリソースを-Azure-にデプロイする"></a>

1. 以下の図に示す [**Azure に配置する**] ボタンをクリックして、このラボの ARM テンプレートとラボ VM のリソースをデプロイします。このリンクは Azure Portal へのディープ リンクとなり、ラボ用のリソースのデプロイに使用する ARM テンプレートにつながります。

    [![Azure に配置するボタン](images/azure-deploy-button-small.png "Azure に配置する")](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FMCW-Modern-cloud-apps%2Fmaster%2FHands-on%20lab%2Fscripts%2Flabvm%2Ftemplate.json)

    >**注**: [**Azure に配置する**] リンクに問題が発生した場合は、ラボ ファイルに含まれる ARM テンプレートの `/Hands-on lab/scripts/labvm/template.json` を使用して、Azure Portal に新たに追加された [**カスタム デプロイ**] からデプロイします。

2. [**カスタム デプロイ**] ブレードで [**リソース グループ**] フィールドの [**新規作成**] を選択し、`ContosoSports-[自身のイニシャルまたは名前]` と入力します。

3. [**Edit parameters**] を選択します。

    ![[Edit parameters] を選択](images/Setup/2019-06-24-17-17-05.png)

4. [**Edit parameters**] ウィンドウで [**ファイルの読み込み**] ボタンをクリックします。

5. 展開したファイルに含まれる `\Hands-on lab\Scripts\labvm\parameters.json` を開きます。

6. [**Save**] をクリックします。

7. [**I agree to the terms and conditions stated above**] チェックボックスをオンにします。

8. [**Purchase**] をクリックします。

    ![[Purchase] をクリック](images/Setup/2019-06-24-17-20-12.png)

9. デプロイには 15 ～ 30 分ほどかかります。その間に次のタスクに進みます。

    [**デプロイ**] リンクから [**Microsoft.Template**] デプロイメントを選択すると、デプロイの進捗状況を表示できます。

    ![テンプレートのデプロイ状況を表示](images/Setup/2019-06-24-17-22-19.png "リソース グループのデプロイ")

    > **注**: SSMS とラボで必要なファイルをインストールする構成スクリプトは、LabVM のデプロイ完了後に実行されます。このタスクはデプロイの進捗状況画面のリストの `LabVM/CustomScriptExtension` という項目に表示されます。次のタスクで LabVM にログインするときには、必要なファイルのダウンロードとインストールが終わりこのタスクが完了するまで待機します。
    >
    > ![デプロイメント タスクのリストで強調表示されている CustomScriptExtension タスク](media/deployment-progress.png "デプロイの進捗状況")

### タスク 3: 環境のリソースを Azure にデプロイする<a name="タスク-3:-環境のリソースを-Azure-にデプロイする"></a>

1. 以下の図に示す [**Azure に配置する**] ボタンをクリックして、このラボの ARM テンプレートと環境のリソースをデプロイします。このリンクは Azure Portal へディープ リンクとなり、ラボ用のリソースのデプロイに使用する ARM テンプレートにつながります。

    [![Azure に配置するボタン.](images/azure-deploy-button-small.png "Azure に配置する")](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FMCW-Modern-cloud-apps%2Fmaster%2FHands-on%20lab%2Fscripts%2Fenvironment%2Ftemplate.json)

    >**注**: [**Azure に配置する**] リンクに問題が発生した場合は、ラボ ファイルに含まれる ARM テンプレートの `/Hands-on lab/scripts/environment/template.json` を使用して、Azure Portal に新たに追加された [**カスタム デプロイ**] からデプロイします。

2. [**カスタム デプロイ**] ブレードで [**リソース グループ**] フィールドの [**新規作成**] を選択し、`contososports[自身のイニシャルまたは名前]`と入力します。

3. [**Edit parameters**] を選択します。

    ![[Edit parameters] を選択](images/Setup/2019-06-24-17-17-05.png)

4. [**Edit parameters**] ウィンドウで [**ファイルの読み込み**] ボタンをクリックします。

5. 展開したファイルに含まれる `\Hands-on lab\Scripts\environment\parameters.json` を開きます。

6. [**Save**] をクリックします。

7. [**カスタム デプロイ**] の [**リージョン**] フィールドで最寄りの Azure リージョンを選択します。

    > **注**: このラボでは [**米国東部**]、[**北ヨーロッパ**]、[**オーストラリア東部**] のいずれかの Azure リージョンをおすすめします。特定の Azure リージョンでは、ARM テンプレートでプロビジョニングされたリソースの一部がサポートされていない場合があります。この制限は、使用する Azure サブスクリプションの種類によっても異なる場合があります。

8. [**I agree to the terms and conditions stated above**] チェックボックスをオンにします。

9. [**Purchase**] をクリックします。

    ![[上記の使用条件に同意する] チェックボックスを音にしてから [Purchase] を選択](images/Setup/2019-06-24-17-20-12.png)

10. デプロイには 5 ～ 10 分ほどかかります。

### タスク 4: Contoso Sports League のサンプルを確認する<a name="タスク-4:-Contoso-Sports-League-のサンプルを確認する"></a>

1. 前の手順でテンプレートを使用してデプロイした **LabVM** に、リモート デスクトップから以下の資格情報で接続します。

    - **管理ユーザー名**: `demouser`
    - **管理パスワード**: `demo@pass123`


    > **注**: **LabVM** 仮想マシンへの接続は、**Lab VM** ARM テンプレートのデプロイが完了してから行います。

2. `C:\MCW` フォルダーを開きます。

3. **MCW** フォルダー内の **Contoso Sports League** フォルダーから `Contoso.Apps.SportsLeague.sln` という Visual Studio ソリューション ファイルを開きます。

4. このソリューションには以下のプロジェクトが含まれます。

    | プロジェクト | 説明 |
    |:----------|:-------------|
    | Contoso.Apps.SportsLeague.Web |   Contoso Sports League の eコマース アプリケーション |
    | Contoso.Apps.SportsLeague.Admin |   Contoso Sports League のコール センターの管理アプリケーション |
    | Contoso.Apps.Common  |   共有層 |
    | Contoso.Apps.SportsLeague.Data  |   共有層 |
    | Contoso.Apps.FunctionApp  |   関数アプリ層 |
    | Contoso.Apps.SportsLeague.Offers |  提供可能な商品のリストを返す API |
    | Contoso.Apps.PaymentGateway   |     支払い処理用 API |

ハンズオン ラボを開始する前に、必ずこのドキュメントの手順をすべて完了してください。
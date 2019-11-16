---
title: プロジェクトに NuGet パッケージを含める
description: このドキュメントでは、Visual Studio for Mac を使用してプロジェクトに NuGet パッケージを含める方法について説明します。 パッケージの検索およびダウンロードの手順を説明し、IDE 統合機能の概要を示します。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: bbff780cda82bb64862d77fe8f407f1803beb876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74127241"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Visual Studio for Mac に NuGet パッケージをインストールして管理する

Visual Studio for Mac 内で NuGet パッケージ マネージャー UI を使用すると、プロジェクトやソリューション内で NuGet パッケージを簡単にインストール、アンインストール、更新することができます。 パッケージを検索し、.NET Core、ASP.NET Core、Xamarin プロジェクトに追加することができます。

この記事では、プロジェクトに NuGet パッケージを含める方法について説明し、プロセスをシームレスにするツール チェーンを示します。

For an intro to using NuGet in Visual Studio for Mac, see [Quickstart: Install and use a package in Visual Studio for Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>パッケージを検索してインストールする

1. Visual Studio for Mac でプロジェクトを開いた状態で、**Solution Pad** 内の **[依存関係]** フォルダー (Xamarin プロジェクトを使用する場合は **[パッケージ]** フォルダー) を右クリックし、 **[NuGet パッケージの管理]** を選択します。

    ![新しい NuGet パッケージのコンテキスト アクションを追加する](media/nuget-walkthrough-packages-menu.png)

2. **[NuGet パッケージの管理]** ウィンドウが起動します。 Ensure that the Source drop-down in the top left corner of the dialog is set to `nuget.org`, so that you're searching the central NuGet package repository.

    ![Nuget パッケージのリスト](media/nuget-walkthrough-add-packages1.png)

3. `EntityFramework` などの特定のパッケージを検索するには、右上隅の検索ボックスを使用します。 使用するパッケージが見つかったら、それを選択し、 **[パッケージを追加]** ボタンをクリックしてインストールを開始します。

    ![EntityFramework NuGet パッケージの追加](media/nuget-walkthrough-add-packages2.png)

4. パッケージはダウンロードされた後、プロジェクトに追加されます。 ソリューションは、編集中のプロジェクトの種類に応じて変化します。

    **Xamarin プロジェクト**
    * **[参照]** ノードには、NuGet パッケージの一部であるすべてのアセンブリのリストが含まれます。
    * **[パッケージ]** ノードには、ダウンロードした各 NuGet パッケージが表示されます。 このリストのパッケージを更新したり、削除したりすることができます。
    
    **.NET Core プロジェクト**

    * **[依存関係] > [NuGet]** ノードには、ダウンロードした各 NuGet パッケージが表示されます。 このリストのパッケージを更新したり、削除したりすることができます。

## <a name="using-nuget-packages"></a>NuGet パッケージの使用

NuGet パッケージが追加され、プロジェクト参照が更新されたら、他のプロジェクト参照の場合と同じように API に対してプログラミングできます。

必ず、必要な `using` ディレクティブをファイルの先頭に追加してください。

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>パッケージの更新

パッケージの更新は、 **[依存関係]** ノード (または、Xamarin プロジェクトの場合は **[パッケージ]** ノード) を右クリックすることで、すべて一度に行うことも、パッケージごとに個別に行うこともできます。 新しいバージョンの NuGet パッケージが使用可能になると、更新アイコンが表示されます ![丸で囲まれた上向きの矢印](media/nuget-walkthrough-update-icon.png)。

コンテキスト メニューにアクセスするには、 **[依存関係]** を右クリックして、 **[更新]** を選択し、すべてのパッケージを更新します。

![パッケージ メニュー](media/nuget-walkthrough-packages-menu-update.png)

* **[NuGet パッケージの管理]** - プロジェクトにさらにパッケージを追加するためのウィンドウが開きます。
* **[更新]** - 各パッケージのソース サーバーを確認し、新しいバージョンをダウンロードします。
* **[復元]** - 不足しているパッケージをダウンロードします (既存のパッケージを新しいバージョンに更新しません)。

更新オプションと復元オプションはソリューション レベルでも使用でき、ソリューション内のすべてのプロジェクトに影響します。

### <a name="locating-outdated-packages"></a>Locating outdated packages
Solution Pad から、現在インストールされているパッケージのバージョンを表示し、更新するパッケージを右クリックすることができます。

![[更新]、[削除]、[更新] のオプションが表示されている [パッケージ] メニュー](media/nuget-walkthrough-PackageMenu.png)

パッケージの新しいバージョンが利用可能な場合は、パッケージ名の横に通知が表示されるので、更新するかどうかを決定できます。

![新しいパッケージ バージョンが利用可能になったときに表示される通知](media/nuget-walkthrough-package-update-available.png)

表示されるメニューには、次の 2 つのオプションがあります。

* **[更新]** - ソース サーバーを確認し、新しいバージョン (存在する場合) をダウンロードします。
* **[削除]** - このプロジェクトからパッケージを削除し、プロジェクトの参照から関連するアセンブリを削除します。

## <a name="manage-packages-for-the-solution"></a>ソリューションのパッケージの管理

ソリューションのパッケージの管理は、複数のプロジェクトを同時に操作するための便利な手段です。

1. Right-click the solution and select **Manage NuGet Packages...** :

    ![ソリューションの NuGet パッケージの管理](media/nuget-walkthrough-manage-packages-solution.png)

1. ソリューションのパッケージを管理する場合、UI を利用して、操作によって影響を与えるプロジェクトを選択できます。

    ![ソリューションのパッケージを管理する場合のプロジェクト セレクター](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>[統合] タブ

When working in a solution with multiple projects, it's considered a best practice to make sure that anywhere you use the same NuGet package in each project, you're also using the same version number of that package. Visual Studio for Mac helps make this easier by providing a **Consolidate** tab in the Package Manager UI when you choose to manage packages for a solution. Using this tab, you can easily see where packages with distinct version numbers are used by different projects in the solution:

![パッケージ マネージャー UI の [統合] タブ](media/nuget-walkthrough-consolidate-tab.png)

In this example, the NuGetDemo project is using Microsoft.EntityFrameworkCore 2.20, whereas NuGetDemo.Shared is using Microsoft.EntityFrameworkCore 2.2.6. パッケージ バージョンを統合するには、次を実行します。

- プロジェクトの一覧で、更新するプロジェクトを選択します。
- Select the version to use in all those projects in the **New Version** list, such as Microsoft.EntityFrameworkCore 3.0.0.
- Select the **Consolidate Package** button.

パッケージ マネージャーによって、選択されたすべてのプロジェクトに対して、選択されたパッケージ バージョンがインストールされます。パッケージは **[統合]** タブ上には表示されなくなります。

## <a name="adding-package-sources"></a>パッケージ ソースの追加

Packages available for installation are initially retrieved from nuget.org. However, you can add other package locations to Visual Studio for Mac. これは、開発中の独自の NuGet パッケージをテストする場合や、会社または組織内でプライベートの NuGet サーバーを使用する場合に便利です。

Visual Studio for Mac で、 **[Visual Studio]、[基本設定]、[NuGet]、[ソース]** の順に移動し、パッケージ ソースのリストを表示して編集します。 ソースはリモート サーバー (URL で指定) またはローカル ディレクトリである場合があります。

![パッケージ ソース](media/nuget-walkthrough-PackageSource.png)

**[追加]** をクリックして新しいソースをセットアップします。 パッケージ ソースのフレンドリ名と URL (またはファイル パス) を入力します。 ソースがセキュリティで保護された Web サーバーの場合は、ユーザー名とパスワードも入力します。それ以外の場合はこれらの項目を空白のままにします。

![パッケージ ソースを追加する](media/nuget-walkthrough-PackageSource2.png)

パッケージを検索する際に、以下のようにさまざまなソースを選択することができます。

![パッケージ ソースを追加する](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>バージョン コントロール

NuGet のドキュメントでは、[ソース管理にパッケージをコミットせずに NuGet を使用する方法](/nuget/consume-packages/packages-and-source-control)について説明しています。 ソース管理でバイナリおよび未使用の情報を格納しない場合は、自動的にサーバーからパッケージを復元するように Visual Studio for Mac を構成することができます。 これは、開発者が初めてソース管理からプロジェクトを取得するときに、Visual Studio for Mac が自動的に必要なパッケージをダウンロードしてインストールすることを意味します。

![パッケージを自動的に復元する](media/nuget-walkthrough-AutoRestore.png)

`packages` ディレクトリを追跡対象から除外する方法の詳細については、特定のソース管理のドキュメントを参照してください。

## <a name="related-video"></a>関連ビデオ

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>関連項目

* [Visual Studio でパッケージをインストールして使用する (Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

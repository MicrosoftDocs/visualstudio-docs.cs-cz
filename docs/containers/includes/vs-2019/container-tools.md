---
title: Visual Studio Tools for Docker と ASP.NET Core
author: ghogen
description: Visual Studio 2019 ツールと Docker for Windows を使用する方法について説明します
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 7eae92f7c65208dfeda9cd19e14eaa627e12a22a
ms.sourcegitcommit: bbff780cda82bb64862d77fe8f407f1803beb876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142188"
---
Visual Studio を使用すると、コンテナー化された ASP.NET Core アプリを簡単にビルド、デバッグ、および実行して、Azure Container Registry (ACR)、Docker Hub、Azure App Service、または独自のコンテナー レジストリに発行することができます。 この記事では、ACR に発行します。

## <a name="prerequisites"></a>必要条件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web 開発**、**Azure Tools** ワークロード、および/または **.NET Core クロスプラットフォーム開発**ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2.2 を使って開発するための [.NET Core 2.2 開発ツール](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* Azure Container Registry に発行する場合、Azure サブスクリプション。 [無料試用版にサインアップします](https://azure.microsoft.com/offers/ms-azr-0044p/)。

## <a name="installation-and-setup"></a>インストールとセットアップ

For Docker installation, first review the information at [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). 次に、[Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows) をインストールします。

## <a name="add-a-project-to-a-docker-container"></a>Docker コンテナーにプロジェクトを追加する

1. **[ASP.NET Core Web アプリケーション]** テンプレートを使って新しいプロジェクトを作成します。
1. **[Web アプリケーション]** を選択し、 **[Enable Docker Support]\(Docker サポートを有効にする\)** チェックボックスがオンになっていることを確認します。

   ![[Enable Docker Support]\(Docker サポートを有効にする\) チェック ボックス](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. コンテナーの種類 (Windows または Linux) を選択し、 **[作成]** をクリックします。

## <a name="dockerfile-overview"></a>Dockerfile の概要

*Dockerfile* (Docker の最終イメージを作成するためのレシピ) は、プロジェクトで作成されます。 その中に含まれるコマンドの詳細については、「[Dockerfile reference](https://docs.docker.com/engine/reference/builder/)」 (Dockerfile リファレンス) を参照してください。

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

前の *Dockerfile* は、[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージに基づいており、プロジェクトをビルドしてコンテナーに追加することで基本イメージを変更するための手順が含まれています。

新しいプロジェクト ダイアログの **[Configure for HTTPS]\(HTTPS 用に構成する\)** チェック ボックスがオンになっている場合、*Dockerfile* は 2 つのポートを公開します。 1 つのポートは HTTP トラフィック用、もう 1 つのポートは HTTPS 用に使用されます。 チェック ボックスがオンになっていない場合は、HTTP トラフィック用に単一のポート (80) が公開されます。

## <a name="debug"></a>デバッグ

ツールバーのデバッグ ドロップダウンから **[Docker]** を選択し、アプリのデバッグを開始します。 証明書の信頼を求めるメッセージが表示される場合があります。続行するには、証明書を信頼することを選びます。

**[出力]** ウィンドウの **[コンテナー ツール]** オプションに、実行されているアクションの内容が表示されます。

**[ツール]** メニュー、[NuGet パッケージ マネージャー]、 **[パッケージ マネージャー コンソール]** の順に選択して、 **[パッケージ マネージャー コンソール]** (PMC) を開きます。

アプリの結果の Docker イメージは、*dev* としてタグ付けされます。 このイメージは、*microsoft/dotnet* 基本イメージの *2.2-aspnetcore-runtime* タグに基づいています。 **パッケージ マネージャー コンソール** (PMC) ウィンドウで `docker images` コマンドを実行します。 コンピューター上のイメージが表示されます。

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **[デバッグ]** 構成ではボリュームのマウントを使用して、反復編集とデバッグ操作を提供するため、**dev** イメージにはアプリのバイナリやその他のコンテンツは含まれません。 すべてのコンテンツを含む実稼働イメージを作成するには、 **[リリース]** 構成を使用します。

PMC で `docker ps` コマンドを実行します。 アプリがコンテナーを使用して実行されていることがわかります。

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="containers-window"></a>Containers window

If you have Visual Studio 2019 version 16.4 or later, you can use the **Containers** window to view running containers on your machine, as well as images that you have available.

Open the **Containers** window by using the search box in the IDE (press **Ctrl**+**Q** to use it), type in `container`, and choose the **Containers** window from the list.

You can mount the **Containers** window in a convenient place, such as below the editor, by moving it around and following the window placement guides.

In the window, find your container and step through each tab to view the environment variables, port mappings, logs, and the filesystem.

For more information, see [View and diagnose containers and images in Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Docker イメージの発行

アプリの開発とデバッグのサイクルが完了すると、アプリの実稼働イメージを作成できます。

1. 構成ドロップダウンを **[リリース]** に変更し、アプリを構築します。
1. **ソリューション エクスプローラー**で対象のプロジェクトを右クリックし、 **[発行]** を選択します。
1. 発行先ダイアログで **[コンテナー レジストリ]** タブを選択します。
1. **[新しい Azure コンテナー レジストリを作成する]** を選択し、 **[発行]** をクリックします。
1. **[新しい Azure コンテナー レジストリを作成する]** で、目的の値を入力します。

    | 設定      | 推奨値  | 説明                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS プレフィックス** | グローバルに一意の名前 | コンテナー レジストリを一意に識別する名前。 |
    | **サブスクリプション** | サブスクリプションの選択 | 使用する Azure のサブスクリプション。 |
    | **[リソース グループ](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  コンテナー レジストリを作成するリソース グループの名前。 新しいリソース グループを作成する場合は、 **[新規]** を選択します。|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | 標準 | コンテナー レジストリのサービス層  |
    | **レジストリの場所** | 近くの場所 | [[地域]](https://azure.microsoft.com/regions/) で、自分に近いか、またはコンテナー レジストリを使用する他のサービスに近い場所を選択します。 |

    ![Visual Studio の Azure コンテナー レジストリを作成するダイアログ][0]

1. **[作成]**

   ![発行の成功を示すスクリーンショット](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>次のステップ

これでレジストリからコンテナーを、[Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app) などの Docker イメージを実行できるホストにプルできるようになりました。

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png

---
title: Windows での Visual Studio コンテナー ツール
description: Docker を操作するために Visual Studio で使用できるツールについて説明します
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 312c827c3b748e10951b243070f43cce559e3a60
ms.sourcegitcommit: bbff780cda82bb64862d77fe8f407f1803beb876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74127187"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio のコンテナー ツール

Visual Studio に含まれるコンテナーを使った開発用のツールは、使いやすく、コンテナー化されたアプリケーションのビルド、デバッグ、配置を大幅に簡略化できます。 1 つのプロジェクトに対して 1 つのコンテナーを使用したり、Docker Compose、Service Fabric、または Kubernetes と共にコンテナーのオーケストレーションを使って、コンテナー内で複数のサービスを使用したりできます。

::: moniker range="vs-2017"

## <a name="prerequisites"></a>必要条件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web 開発**、**Azure Tools** ワークロード、かつ/または **.NET Core クロスプラットフォーム開発**ワークロードがインストールされた [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Azure Container Registry に発行する場合、Azure サブスクリプション。 [無料試用版にサインアップします](https://azure.microsoft.com/offers/ms-azr-0044p/)。

## <a name="docker-support-in-visual-studio"></a>Visual Studio での Docker サポート

Docker サポートは、ASP.NET プロジェクト、ASP.NET Core プロジェクト、.NET Core と .NET Framework のコンソール プロジェクトで利用できます。

Visual Studio での Docker のサポートは、お客様のニーズに応じて、多数のリリースを経て変更されてきました。 プロジェクトに追加できる Docker サポートには 2 つのレベルがあり、サポートされるオプションはプロジェクトの種類と Visual Studio のバージョンによって異なります。 サポートされている一部のプロジェクトの種類では、オーケストレーションなしで 1 つのプロジェクト用に 1 つのコンテナーを使いたいだけの場合は、Docker サポートを追加することでこれを実行できます。  次のレベルは、コンテナー オーケストレーションのサポートです。これは、選択した特定のオーケストレーター用の適切なサポート ファイルを追加します。  

Visual Studio 2017 では、コンテナー オーケストレーション サービスとして Docker Compose と Service Fabric を使用できます。  [Visual Studio Tools for Kubernetes](https://aka.ms/get-vsk8stools) をインストールする場合は、Kubernetes も使用できます。

> [!NOTE]
> 15.8 より前のバージョンの Visual Studio 2017 を使うか、.NET Framework プロジェクト テンプレート (.NET Core ではなく) を使う場合は、Docker サポートを追加するときに、Docker Compose を使うオーケストレーションのサポートが自動的に追加されます。 Visual Studio 2017 バージョン 15.0 から 15.7 と、.NET Framework プロジェクトに対しては、Docker Compose を使ったコンテナー オーケストレーションのサポートが自動的に追加されます。

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>必要条件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web 開発**、**Azure Tools** ワークロード、および/または **.NET Core クロスプラットフォーム開発**ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2.2 を使って開発するための [.NET Core 2.2 開発ツール](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* Azure Container Registry に発行する場合、Azure サブスクリプション。 [無料試用版にサインアップします](https://azure.microsoft.com/offers/ms-azr-0044p/)。

## <a name="docker-support-in-visual-studio"></a>Visual Studio での Docker サポート

Docker サポートは、ASP.NET プロジェクト、ASP.NET Core プロジェクト、.NET Core と .NET Framework のコンソール プロジェクトで利用できます。

Visual Studio での Docker のサポートは、お客様のニーズに応じて、多数のリリースを経て変更されてきました。 プロジェクトに追加できる Docker サポートには 2 つのレベルがあり、サポートされるオプションはプロジェクトの種類と Visual Studio のバージョンによって異なります。 サポートされている一部のプロジェクトの種類では、オーケストレーションなしで 1 つのプロジェクト用に 1 つのコンテナーを使いたいだけの場合は、Docker サポートを追加することでこれを実行できます。  次のレベルは、コンテナー オーケストレーションのサポートです。これは、選択した特定のオーケストレーター用の適切なサポート ファイルを追加します。  

Visual Studio 2019 では、コンテナー オーケストレーション サービスとして Docker Compose、Kubernetes、Service Fabric を使用できます。

> [!NOTE]
> 完全な .NET Framework コンソール プロジェクト テンプレートを使う場合は、Docker サポートを追加するときに、Docker Compose を使うオーケストレーションのサポートが自動的に追加されます。

In Visual Studio 2019 version 16.4 and later, the **Containers** window is available, which lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment. See [View and diagnose containers and images in Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Docker サポートの追加

次のスクリーンショットに示すように、新しいプロジェクトを作成するときに **[Enable Docker Support]\(Docker サポートを有効にする\)** を選択することで、プロジェクトの作成中に Docker サポートを有効にすることができます。

::: moniker range="vs-2017"
![Visual Studio で新しい ASP.NET Core Web アプリの Docker サポートを有効にする](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio で新しい ASP.NET Core Web アプリの Docker サポートを有効にする](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> (.NET Core ではなく) .NET Framework プロジェクトの場合、Windows コンテナーのみを使用できます。

既存のプロジェクトに Docker サポートを追加するには、**ソリューション エクスプローラー**で **[追加]**  >  **[Docker のサポート]** の順に選択します。 **[追加] > [Docker のサポート]** と **[追加] > [コンテナー オーケストレーター サポート]** コマンドは、**ソリューション エクスプローラー**の ASP.NET Core プロジェクトのプロジェクト ノードの右クリック メニュー (またはコンテキスト メニュー) にあります。次のスクリーンショットを参照してください。

![Visual Studio の Docker サポートの追加メニュー オプション](./media/overview/add-docker-support-menu.png)

Docker サポートを追加または有効にすると、Visual Studio により以下がプロジェクトに追加されます。

- *Dockerfile* ファイル
- .dockerignore ファイル
- Microsoft.VisualStudio.Azure.Containers.Tools.Targets に対する NuGet パッケージ参照

::: moniker range=">=vs-2019"
Docker サポートを追加すると、ソリューションは次のようになります。

![Dockerfile と .dockerignore ファイルを含むソリューション エクスプローラーのスクリーンショット](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> 以下のスクリーンショットに示すように、ASP.NET プロジェクト (.NET Framework.NET Core プロジェクトではありません) 用のプロジェクトの作成中に Docker のサポートを有効にすると、コンテナー オーケストレーションのサポートも追加されます。

![ASP.NET プロジェクトで Docker 構成のサポートを有効にする](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose のサポート

Docker Compose を使って複数コンテナーのソリューションを構成する場合は、コンテナー オーケストレーションのサポートをプロジェクトに追加します。 これにより、コンテナーのグループ (ソリューション全体、またはプロジェクトのグループ) が同じ *docker-compose.yml* ファイル内で定義されている場合、それらを同時に実行およびデバッグすることができます。

Docker Compose を使ったコンテナー オーケストレーションのサポートを追加するには、**ソリューション エクスプローラー**でソリューションまたはプロジェクトのノードを右クリックし、 **[追加] > [Container Orchestration Support]\(コンテナー オーケストレーション サポート\)** の順に選択します。 次に、 **[Docker Compose]** を選択してコンテナーを管理します。

プロジェクトにコンテナー オーケストレーションのサポートを追加すると、次に示すように、(既になかった場合) プロジェクトに *Dockerfile* が追加され、**ソリューション エクスプローラー**内のソリューションに **docker-compose** フォルダーが追加されるのを確認できます。

![Visual Studio のソリューション エクスプローラーの Docker ファイル](media/overview/docker-support-solution-explorer.png)

*docker-compose.yml* が既に存在する場合、Visual Studio により、構成コードの必要な行が単にそれに追加されます。

Docker Compose を使って制御したい他のプロジェクトで、このプロセスを繰り返します。

## <a name="kubernetes-support"></a>Kubernetes のサポート

::: moniker range="vs-2017"
Kubernetes のサポートを追加するには、[Visual Studio Tools for Kubernetes](https://aka.ms/get-vsk8stools) をインストールします。
::: moniker-end

Kubernetes のサポートでは、ローカル プロジェクトと、[Azure Kubernetes Service (AKS)](/azure/aks) で実行されている Kubernetes クラスターの間の接続を有効にし、それにより Visual Studio を使って AKS で実行されているサービスを変更およびデバッグできます。  このサービスは [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio) によって提供されます。 Azure Dev Spaces では、"*開発スペース*" と呼ばれる Kubernetes サービスの別のブランチを開発のために設定することもできます。そのため、開発中に運用サービスを作業中のバージョンから効率的に分離して、個別の変更が互いに明確に分離される状態を維持することができます。

プロジェクトに Kubernetes のサポートを追加するには、コンテナー オーケストレーションのサポートを追加するときに **[Kubernetes/Helm]** を選択します。 いくつかのファイルがプロジェクトに追加されます。これには、Azure Dev Spaces を構成する *azds.yaml* や、Kubernetes サービスの構造を説明する Helm Chart が含まれます。

## <a name="service-fabric-support"></a>Service Fabric のサポート

Visual Studio の Service Fabric ツールを使うと、Azure Service Fabric 用に開発とデバッグを行い、ローカルで実行およびデバッグし、Azure に配置することができます。

::: moniker range="vs-2017"
Azure 開発ワークロードがインストールされた Visual Studio 2017 バージョン 15.9 以降では、Windows コンテナーと Service Fabric のオーケストレーションを使った、コンテナー化されたマイクロサービスの開発がサポートされます。
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 では、Windows コンテナーと Service Fabric のオーケストレーションを使った、コンテナー化されたマイクロサービスの開発がサポートされています。
::: moniker-end

For a detailed tutorial, see [Tutorial: Deploy a .NET application in a Windows container to Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Azure Service Fabric の詳細については、[Service Fabric](/azure/service-fabric) に関するページをご覧ください。

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>継続的デリバリーと継続的インテグレーション (CI/CD)

サービスのコードと構成の変更に関する自動化された継続的なインテグレーションとデリバリーのために、Visual Studio は簡単に Azure Pipelines と統合できます。 開始するには、「[Create your first pipeline (最初のパイプラインを作成する)](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)」をご覧ください。

For Service Fabric, see [Tutorial: Deploy your ASP.NET Core app to Azure Service Fabric by using Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Kubernetes については、「[Deploy a Docker container app to Azure Kubernetes Service (Azure Kubernetes Service に Docker コンテナー アプリをデプロイする)](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops)」をご覧ください。

## <a name="next-steps"></a>次のステップ

サービスの実装と、コンテナーを操作するための Visual Studio ツールの使用方法について詳しくは、以下の記事をご覧ください。

[ローカルの Docker コンテナーでアプリをデバッグする](edit-and-refresh.md)

[Visual Studio を使用して ASP.NET Docker コンテナーをコンテナー レジストリにデプロイする](hosting-web-apps-in-docker.md)

---
title: Nasazení kontejneru Docker ASP.NET do registru ACR
description: Naučte se používat nástroje sady Visual Studio Container k nasazení webové aplikace ASP.NET nebo ASP.NET Core do registru kontejneru.
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 74a74e17dcc909b529a0afad1d66959000c80455
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859538"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio

## <a name="overview"></a>Přehled

Docker je odlehčený modul kontejnerů, podobně jako některé z různých způsobů virtuálního počítače, který můžete použít k hostování aplikací a služeb.
V tomto kurzu se seznámíte s použitím sady Visual Studio k publikování vašich kontejnerových aplikací na [Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Pokud ještě nemáte předplatné Azure, vytvořte si napřed [bezplatný účet](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Požadavky

Pro absolvování tohoto kurzu potřebujete:

::: moniker range="vs-2017"
* Nainstalujte si nejnovější verzi sady [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)s úlohou vývoj ASP.NET a webu.
::: moniker-end
::: moniker range=">=vs-2019"
* Nainstalujte si nejnovější verzi sady [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s úlohou vývoj ASP.NET a webu.
::: moniker-end
* Nainstalovat [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Vytvoření webové aplikace ASP.NET Core

Následující kroky vás provedou vytvořením základní aplikace ASP.NET Core, která se bude používat v tomto kurzu. Pokud již máte projekt, můžete tuto část přeskočit.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Publikování kontejneru do Azure Container Registry

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
2. V dialogovém okně **Publikovat cíl** vyberte možnost **Container Registry**.
3. Vyberte **nový Azure Container Registry** a klikněte na **publikovat**.
4. Do pole **vytvořit nový Azure Container Registry** zadejte požadované hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Klikněte na **Vytvořit**.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Publikování kontejneru do Azure Container Registry
1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
2. V dialogovém okně **publikovat** vyberte **Docker Container Registry**.

   ![Snímek obrazovky s dialogem publikovat – vyberte Docker Container Registry](media/container-tools/vs-2019/docker-container-registry.png)

3. Vyberte **vytvořit novou Azure Container Registry**.
 
   ![Snímek obrazovky dialogového okna pro publikování – vyberte vytvořit novou Azure Container Registry](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Zadejte požadované hodnoty na obrazovce **Azure Container Registry** .

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Klikněte na **Vytvořit**.

6. Kliknutím na **Dokončit** proces dokončete.
::: moniker-end

Kontejner teď můžete načíst z registru do libovolného hostitele, který podporuje spouštění imagí Docker, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Viz také

[Rychlý Start: nasazení instance kontejneru v Azure pomocí rozhraní příkazového řádku Azure](/azure/container-instances/container-instances-quickstart)

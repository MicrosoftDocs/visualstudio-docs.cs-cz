---
title: Nasazení kontejneru ASP.NET Dockeru do registru ACR
description: Zjistěte, jak pomocí nástrojů kontejneru Sady Visual Studio nasadit ASP.NET nebo ASP.NET webovou aplikaci Core do registru kontejnerů.
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916916"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio

## <a name="overview"></a>Přehled

Docker je lehký modul kontejneru, v některých ohledech podobný virtuálnímu počítači, který můžete použít k hostování aplikací a služeb.
Tento kurz vás provede pomocí Sady Visual Studio k publikování kontejnerizované aplikace do [registru kontejnerů Azure](https://azure.microsoft.com/services/container-registry).

Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet,](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) než začnete.

## <a name="prerequisites"></a>Požadavky

Pro absolvování tohoto kurzu potřebujete:

::: moniker range="vs-2017"
* Instalace nejnovější verze [Visual Studia 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)s úlohou "ASP.NET a vývoj webových aplikací"
::: moniker-end
::: moniker range=">=vs-2019"
* Instalace nejnovější verze [Visual Studia 2019](https://visualstudio.microsoft.com/downloads) s úlohou "ASP.NET a vývoj webových aplikací"
::: moniker-end
* Instalace [Dockeru pro Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Vytvoření webové aplikace ASP.NET Core
Následující kroky vás provedou vytvořením základní aplikace ASP.NET Core, která se bude používat v tomto kurzu. Pokud již máte projekt, můžete tuto část přeskočit.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Publikování kontejneru do registru kontejnerů Azure
1. Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a zvolte **Publikovat**.
2. V dialogovém okně publikovat cíl vyberte kartu **Registr kontejneru.**
3. Zvolte **Nový registr kontejnerů Azure** a klikněte na **Publikovat**.
4. Vyplňte požadované hodnoty v **registru vytvořit nový kontejner Azure**.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jednoznačně identifikuje registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve kterém chcete vytvořit registr kontejneru. Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění v blízkosti vás | Zvolte umístění v [oblasti](https://azure.microsoft.com/regions/) ve vašem okolí nebo v blízkosti jiných služeb, které budou používat registr kontejnerů. |

    ![Dialogové okno Vytvořit registr kontejnerů Azure v Sadě Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Klikněte na **Vytvořit.**

Nyní můžete vytáhnout kontejner z registru na libovolného hostitele schopného spouštět ibi Dockeru, například [instance kontejneru Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Viz také

[Úvodní příručka: Nasazení instance kontejneru v Azure pomocí azure cli](/azure/container-instances/container-instances-quickstart)

---
title: Nasazení kontejneru Dockeru ASP.NET do Azure Container Registry (ACR) | Dokumentace Microsoftu
description: Zjistěte, jak nasadit webovou aplikaci ASP.NET Core do registru kontejnerů pomocí Visual Studio Tools for Docker
services: azure-container-service
documentationcenter: .net
author: mlearned
manager: douge
editor: ''
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.service: azure-container-service
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 05/21/2018
ms.author: mlearned
ms.openlocfilehash: a033f60d636be8d1e093bf06ee757e0520368a53
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248183"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio
## <a name="overview"></a>Přehled
Docker je modul jednoduchý kontejner, podobně jako v některých ohledech k virtuálnímu počítači, který můžete použít k hostování aplikací a služeb.
Tento kurz vás provede kontejnerizované aplikace můžete publikovat pomocí sady Visual Studio [Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Pokud ještě nemáte předplatné Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) před tím, než začnete.

## <a name="prerequisites"></a>Požadavky
K provedení kroků v tomto kurzu je potřeba:

* Nainstalujte nejnovější verzi [Visual Studio 2017](https://azure.microsoft.com/downloads/) s úlohou "vývoj aplikací ASP.NET a web"
* Nainstalujte [Docker pro Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="1-create-an-aspnet-core-web-app"></a>1. Vytvoření webové aplikace ASP.NET Core
Následující kroky vás provedou vytvořením základní aplikaci ASP.NET Core, který se použije v tomto kurzu.

[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-publish-your-container-to-azure-container-registry"></a>2. Publikování vašeho kontejneru do služby Azure Container Registry
1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a zvolte **publikovat**.
2. V dialogovém okně Publikovat cíl, vyberte **Container Registry** kartu.
3. Zvolte **nový registr kontejneru Azure** a klikněte na tlačítko **publikovat**.
4. Vyplňte požadované hodnoty v **vytvořit nový registr kontejneru Azure**.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jednoznačně identifikuje vašeho registru kontejneru. |
    | **Předplatné** | Vaše předplatné | Předplatné Azure používat. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve kterém chcete vytvořit registr kontejnerů. Zvolte **nový** vytvořit novou skupinu prostředků.|
    | **[SKLADOVÁ POLOŽKA](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Úrovně služby do registru kontejneru  |
    | **Umístění registru** | Vám nejbližším místě | Zvolte umístění, do [oblasti](https://azure.microsoft.com/regions/) vaší blízkosti nebo v blízkosti jiných služeb, které budou používat službu container registry. |

    ![Visual Studio vytvořit dialogové okno Azure Container Registry][0]

5. Klikněte na **Vytvořit**.

Můžete nyní využít kontejneru z registru na každém hostiteli podporuje spuštění imagí Dockeru, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png

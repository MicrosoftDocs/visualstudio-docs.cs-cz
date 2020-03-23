---
title: Publikování do Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806907"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikování webové aplikace do služby Azure App Service pomocí sady Visual Studio

Pro ASP.NET ASP.NET core, Node.js a .NET Core aplikace, publikovat do služby Azure App Service nebo Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro jednorázové (nebo ruční) nasazení aplikací použijte nástroj **publikování** v Sadě Visual Studio k nasazení ASP.NET, ASP.NET Core, Node.js a .NET Core aplikace do služby Azure App Service nebo App Service pro Linux (pomocí kontejnerů). U aplikací v Pythonu postupujte podle kroků v [Pythonu – publikování do služby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Tento článek popisuje, jak používat nástroj **publikování** pro jednorázové nasazení.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat** (nebo použijte položku nabídky**Publikovat** **sestavení).** > 

    ![Příkaz Publikovat v kontextové nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "Zvolte Publikovat")

1. Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat** a v takovém případě vyberte **možnost Vytvořit nový profil**.

1. V **dialogovém** okně Vybrat cíl publikování zvolte **Služba aplikace**.

    ![Zvolte službu Azure App Service](../deployment/media/quickstart-publish-azure.png "Zvolte službu Azure App Service")

1. Vyberte **Publikovat**. Zobrazí se dialogové okno **Vytvořit službu App Service.** V případě potřeby se přihlaste pomocí účtu Azure a pole naplní výchozí nastavení služby app service.

    ![Vytvoření služby App Service](../deployment/media/quickstart-publish-settings-app-service.png "Vytvoření služby Azure App Service")

1. Vyberte **Vytvořit**. Visual Studio nasadí aplikaci do služby Azure App Service a webová aplikace se načte ve vašem prohlížeči. Podokno **Publikování** vlastností projektu zobrazuje adresu URL webu a další podrobnosti.

    ![Podokno vlastností publikování se souhrnem profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud předpokládáte, že už tyto prostředky nebudete potřebovat, můžete je odstranit tak, že odstraníte skupinu prostředků.
Na webu Azure Portal v nabídce vlevo vyberte **Skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupiny prostředků zkontrolujte, že chcete všechny uvedené prostředky odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a potom vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste se naučili, jak pomocí Sady Visual Studio vytvořit profil publikování pro nasazení do Azure. Profil publikování můžete také nakonfigurovat importem nastavení publikování ze služby Azure App Service.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do Azure](tutorial-import-publish-settings-azure.md)

---
title: Publikovat do služby App Service na Linuxu
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806870"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikování aplikace ASP.NET Core do služby App Service na Linuxu pomocí Visual Studia

Počínaje Visual Studio 2017 verze 15.7, můžete publikovat ASP.NET základní aplikace do Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro jednorázové (nebo ruční) nasazení aplikací, použijte nástroj **publikovat** ve Visual Studiu publikovat ASP.NET základní aplikace pro App Service pro Linux (pomocí kontejnerů).

Tento článek popisuje, jak používat nástroj **publikování** pro jednorázové nasazení.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikovat do služby App Service na Linuxu

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat** (nebo použijte položku nabídky**Publikovat** **sestavení).** > 

    ![Příkaz Publikovat v kontextové nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "Zvolte Publikovat")

1. Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat** a v takovém případě vyberte **možnost Vytvořit nový profil**.

1. V **dialogovém** okně Vybrat cíl publikování zvolte **App Service Linux**.

    ![Zvolte službu Azure App Service](../deployment/media/quickstart-publish-linux.png "Zvolte službu Azure App Service")

1. Vyberte **Publikovat**. Zobrazí se dialogové okno **Vytvořit službu App Service.** V případě potřeby se přihlaste pomocí účtu Azure a pole naplní výchozí nastavení služby app service.

    ![Vytvoření služby App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Vytvoření služby Azure App Service")

1. Vyberte **Vytvořit**. Visual Studio nasadí aplikaci do služby Azure App Service a webová aplikace se načte ve vašem prohlížeči. Podokno **Publikování** vlastností projektu zobrazuje adresu URL webu a další podrobnosti.

    ![Podokno vlastností publikování se souhrnem profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud předpokládáte, že už tyto prostředky nebudete potřebovat, můžete je odstranit tak, že odstraníte skupinu prostředků.
Na webu Azure Portal v nabídce vlevo vyberte **Skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupiny prostředků zkontrolujte, že chcete všechny uvedené prostředky odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a potom vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste se naučili, jak pomocí sady Visual Studio vytvořit profil publikování pro nasazení služby App Service v Linuxu. Můžete chtít další informace o publikování na Linux pomocí Azure.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)

---
title: Publikování na App Service v systému Linux
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
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806870"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikování aplikace ASP.NET Core pro App Service v systému Linux pomocí sady Visual Studio

Počínaje verzí Visual Studio 2017 verze 15,7 můžete publikovat aplikace ASP.NET Core pro Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro účely jednorázového (nebo ručního) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio k publikování ASP.NET Corech aplikací pro App Service pro Linux (pomocí kontejnerů).

Tento článek popisuje, jak používat nástroj pro **publikování** pro nasazení v jednom čase.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikování na App Service v systému Linux

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte položku nabídky **sestavit** > **publikovat** ).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste dříve nakonfigurovali nějaké publikační profily, otevře se podokno **publikování** . v takovém případě vyberte **vytvořit nový profil**.

1. V dialogovém okně **vybrat cíl publikování** zvolte možnost **App Service Linux**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-linux.png "Zvolit Azure App Service")

1. Vyberte **publikovat**. Zobrazí se dialogové okno **vytvořit App Service** . Přihlaste se pomocí účtu Azure, pokud je to nutné, a pak výchozí nastavení služby App Service naplní pole.

    ![Vytvořit App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Vytvořit Azure App Service")

1. Vyberte **vytvořit**. Visual Studio nasadí aplikaci do vašeho Azure App Service a webová aplikace se načte v prohlížeči. V podokně **publikování** vlastností projektu se zobrazuje adresa URL webu a další podrobnosti.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud neočekáváte, že tyto prostředky budete potřebovat v budoucnu, můžete je odstranit odstraněním skupiny prostředků.
V nabídce vlevo v Azure Portal vyberte **skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupina prostředků se ujistěte, že jsou uvedené prostředky ty, které chcete odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a pak vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování pro nasazení App Service v systému Linux. Další informace o publikování na Linux můžete získat pomocí Azure.

> [!div class="nextstepaction"]
> [App Service pro Linux](/azure/app-service/containers/app-service-linux-intro)

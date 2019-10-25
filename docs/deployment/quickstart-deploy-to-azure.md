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
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806907"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikování webové aplikace pro Azure App Service pomocí sady Visual Studio

Pro aplikace ASP.NET, ASP.NET Core, Node. js a .NET Core proveďte publikování do Azure App Service nebo Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro jednorázové (nebo ruční) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio k nasazení aplikací ASP.NET, ASP.NET Core, Node. js a .NET Core do Azure App Service nebo App Service pro Linux (pomocí kontejnerů). V případě aplikací Python postupujte podle pokynů v [Pythonu – publikování do Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Tento článek popisuje, jak používat nástroj pro **publikování** pro nasazení v jednom čase.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte položku nabídky **sestavit** > **publikovat** ).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste dříve nakonfigurovali nějaké publikační profily, otevře se podokno **publikování** . v takovém případě vyberte **vytvořit nový profil**.

1. V dialogovém okně **vybrat cíl publikování** zvolte možnost **App Service**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-azure.png "Zvolit Azure App Service")

1. Vyberte **publikovat**. Zobrazí se dialogové okno **vytvořit App Service** . Přihlaste se pomocí účtu Azure, pokud je to nutné, a pak výchozí nastavení služby App Service naplní pole.

    ![Vytvořit App Service](../deployment/media/quickstart-publish-settings-app-service.png "Vytvořit Azure App Service")

1. Vyberte **vytvořit**. Visual Studio nasadí aplikaci do vašeho Azure App Service a webová aplikace se načte v prohlížeči. V podokně **publikování** vlastností projektu se zobrazuje adresa URL webu a další podrobnosti.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud neočekáváte, že tyto prostředky budete potřebovat v budoucnu, můžete je odstranit odstraněním skupiny prostředků.
V nabídce vlevo v Azure Portal vyberte **skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupina prostředků se ujistěte, že jsou uvedené prostředky ty, které chcete odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a pak vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování pro nasazení do Azure. Profil publikování můžete také nakonfigurovat importem nastavení publikování z Azure App Service.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do Azure](tutorial-import-publish-settings-azure.md)

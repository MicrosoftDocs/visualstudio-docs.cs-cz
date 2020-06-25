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
ms.openlocfilehash: 5b0b45d586fb6eb89eb458329f611d980d9415e0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285467"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikování aplikace ASP.NET Core pro App Service v systému Linux pomocí sady Visual Studio

Počínaje verzí Visual Studio 2017 verze 15,7 můžete publikovat aplikace ASP.NET Core pro Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro účely jednorázového (nebo ručního) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio k publikování ASP.NET Corech aplikací pro App Service pro Linux (pomocí kontejnerů).

Tento článek popisuje, jak používat nástroj pro **publikování** pro nasazení v jednom čase.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Publikování na Azure App Service v systému Linux

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky**publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. V dialogovém okně **publikovat** vyberte **Azure**.

    ![Zvolit cíl publikování](../deployment/media/quickstart-publish-azure-new.png)

1. Vyberte **Azure App Service (Linux)** a **Další**.

    ![Zvolit Azure App Service v systému Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. V případě potřeby se přihlaste pomocí účtu Azure. Vyberte **vytvořit nový Azure App Service...**

    ![Odkaz pro vytvoření nové instance Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. V dialogovém okně **vytvořit Azure App Service (Linux)** se naplní pole **název aplikace**, **skupina prostředků**a položka **plánu App Service** . Tyto názvy můžete zachovat nebo je změnit. Až budete připraveni, vyberte **vytvořit**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. V dialogovém okně **publikovat** se nově vytvořená instance automaticky vybrala. Až budete připraveni, klikněte na **Dokončit**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Vyberte **Publikovat**. Visual Studio nasadí aplikaci do vašeho Azure App Service a webová aplikace se načte v prohlížeči. V podokně **publikování** vlastností projektu se zobrazuje adresa URL webu a další podrobnosti.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud předpokládáte, že už tyto prostředky nebudete potřebovat, můžete je odstranit tak, že odstraníte skupinu prostředků.
Na webu Azure Portal v nabídce vlevo vyberte **Skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupiny prostředků zkontrolujte, že chcete všechny uvedené prostředky odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a potom vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování pro nasazení App Service v systému Linux. Další informace o publikování na Linux můžete získat pomocí Azure.

> [!div class="nextstepaction"]
> [App Service pro Linux](/azure/app-service/containers/app-service-linux-intro)

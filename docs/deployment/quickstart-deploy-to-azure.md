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
ms.openlocfilehash: deef5aeaa802d5f5b46ba81f711173dc81a32357
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800304"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikování webové aplikace do služby Azure App Service pomocí sady Visual Studio

Pro aplikace ASP.NET, ASP.NET Core, Node.js a .NET Core publikujte do Azure App Service nebo Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pro jednorázové (nebo ruční) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio k nasazení aplikací ASP.NET, ASP.NET Core, Node.js a .NET Core do Azure App Service nebo App Service pro Linux (pomocí kontejnerů). V případě aplikací Python postupujte podle pokynů v [Pythonu – publikování do Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Tento článek popisuje, jak používat nástroj pro **publikování** pro nasazení v jednom čase.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Publikování do Azure App Service ve Windows

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky**publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. V dialogovém okně **publikovat** vyberte **Azure**.

    ![Zvolit cíl publikování](../deployment/media/quickstart-publish-azure-new.png)

1. Vyberte **Azure App Service (Windows)** a **Další**.

    ![Zvolit Azure App Service v systému Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. V případě potřeby se přihlaste pomocí účtu Azure. Vyberte **vytvořit nový Azure App Service...**

    ![Odkaz pro vytvoření nové instance Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. V dialogovém okně **vytvořit Azure App Service (Windows)** se naplní pole **název aplikace**, **skupina prostředků**a položka **plánu App Service** . Tyto názvy můžete zachovat nebo je změnit. Až budete připraveni, vyberte **vytvořit**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. V dialogovém okně **publikovat** se nově vytvořená instance automaticky vybrala. Až budete připraveni, vyberte **Dokončit**.

    ![Zvolit Azure App Service](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Vyberte **Publikovat**. Visual Studio nasadí aplikaci do vašeho Azure App Service a webová aplikace se načte v prohlížeči. V podokně **publikování** vlastností projektu se zobrazuje adresa URL webu a další podrobnosti.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud předpokládáte, že už tyto prostředky nebudete potřebovat, můžete je odstranit tak, že odstraníte skupinu prostředků.
Na webu Azure Portal v nabídce vlevo vyberte **Skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupiny prostředků zkontrolujte, že chcete všechny uvedené prostředky odstranit.
Vyberte **Odstranit**, do textového pole zadejte **myResourceGroup** a potom vyberte **Odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování pro nasazení do Azure. Profil publikování můžete také nakonfigurovat importem nastavení publikování z Azure App Service.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do Azure](tutorial-import-publish-settings-azure.md)

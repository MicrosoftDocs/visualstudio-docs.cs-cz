---
title: Publikování na App Service v systému Linux
description: Seznamte se s metodami publikování aplikací ASP.NET Core pro Azure App Service Linux pomocí kontejnerů, včetně souvislých a jednorázových možností.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: 0371a4186d51598a79818f79719b58e122a311f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927454"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikování aplikace ASP.NET Core pro App Service v systému Linux pomocí sady Visual Studio

Počínaje verzí Visual Studio 2017 verze 15,7 můžete publikovat aplikace ASP.NET Core pro Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

* Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Pro účely jednorázového (nebo ručního) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio k publikování ASP.NET Corech aplikací pro App Service pro Linux (pomocí kontejnerů).

Tento článek popisuje, jak používat nástroj pro **publikování** pro nasazení v jednom čase.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Publikování na Azure App Service v systému Linux

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte   >  položku nabídky **publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, zobrazí se okno **publikovat** . Vyberte možnost pro **novou** položku.

1. V okně **publikovat** vyberte **Azure**.

    ![Zvolit cíl publikování](../deployment/media/quickstart-publish-azure-new.png)

1. Vyberte **Azure App Service (Linux)** a **Další**.

    ![Zvolit Azure App Service v systému Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. V případě potřeby se přihlaste pomocí účtu Azure. Vyberte **vytvořit nový Azure App Service...**

    ![Odkaz pro vytvoření nové instance Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. V dialogovém okně **vytvořit Azure App Service (Linux)** se naplní pole **název aplikace**, **skupina prostředků** a položka **plánu App Service** . Tyto názvy můžete zachovat nebo je změnit. Až budete připraveni, vyberte **vytvořit**.

    ![Snímek obrazovky s názvem, předplatným, skupinou prostředků a hostovaným polem plánu hostování dialogového okna pro vytvoření Azure App Service (Linux)](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. V dialogovém okně **publikovat** se nově vytvořená instance automaticky vybrala. Až budete připraveni, klikněte na **Dokončit**.

    ![Snímek obrazovky s dialogovým oknem publikovat s nově vytvořenou službou MyASpCoreWebAppOnAzure vybranou jako App Service pro publikování](../deployment/media/quickstart-publish-linux-select-instance.png)

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
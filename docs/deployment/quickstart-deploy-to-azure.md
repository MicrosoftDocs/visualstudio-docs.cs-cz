---
title: Publikování do Azure App Service
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341687"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikování webové aplikace do služby Azure App Service pomocí sady Visual Studio

Můžete použít **publikovat** nástroj k publikování aplikace v ASP.NET, ASP.NET Core, Node.js a .NET Core do Azure App Service nebo Azure App Service pro Linux (použitím kontejnery). Aplikace v Pythonu, postupujte podle kroků [Python - publikovat do služby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

1. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **publikovat** (nebo použijte **sestavení** > **publikovat** položky nabídky).

    ![Příkaz Publikovat v místní nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "tlačítko Publikovat")

1. Pokud jste dříve nakonfigurovali všech profilů publikování **publikovat** otevře se podokno, ve které vyberte případu **vytvořit nový profil**.

1. V **vyberte cíl publikování** dialogového okna zvolte **služby App Service**.

    ![Zvolte Azure App Service](../deployment/media/quickstart-publish-azure.png "zvolte služby Azure App Service")

1. Vyberte **publikovat**. **Vytvořit službu App Service** zobrazí se dialogové okno. Přihlaste se pomocí budete účet Azure, je-li nutné a výchozí nastavení aplikace služby vyplňte pole.

    ![Vytvořit službu App Service](../deployment/media/quickstart-publish-settings-app-service.png "vytvořit službu Azure App Service")

1. Vyberte **vytvořit**. Visual Studio nasadí aplikaci do služby Azure App Service a webovou aplikaci se načte v prohlížeči. Vlastnosti projektu **publikovat** podokně se zobrazí adresa URL webu a další podrobnosti.

    ![Podokno vlastností zobrazuje souhrn profil publikování](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V předchozích krocích jste vytvořili prostředky Azure ve skupině prostředků. Pokud jste Neočekáváme, že v budoucnu potřeba tyto prostředky, můžete je odstranit tak, že odstraníte skupinu prostředků.
V nabídce vlevo na webu Azure Portal vyberte **skupiny prostředků** a pak vyberte **myResourceGroup**.
Na stránce skupiny prostředků Ujistěte se, že všechny uvedené prostředky jsou ty, které chcete odstranit.
Vyberte **odstranit**, typ **myResourceGroup** v textovém poli a pak vyberte **odstranit**.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak vytvořit profil publikování pro nasazení do Azure pomocí sady Visual Studio. Můžete také nakonfigurovat publikování profilu pomocí importu nastavení publikování z Azure App Service.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do Azure](tutorial-import-publish-settings-azure.md)

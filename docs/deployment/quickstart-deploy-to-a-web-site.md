---
title: Publikování na webu
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173677"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikování webové aplikace na webu pomocí sady Visual Studio

Pomocí nástroje **publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python na web ze sady Visual Studio. Pro Node. js je postup podporován, ale uživatelské rozhraní je jiné.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci pro Windows do síťové sdílené složky, přečtěte si téma [nasazení desktopové aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLR naleznete informace v tématu [nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo pro C/C++ viz [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikování na webu

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky**publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Vyberte **vytvořit nový profil**.

1. V dialogovém okně **publikovat** vyberte možnost **webový server (IIS)**.

    ![Zvolit cíl publikování](../deployment/media/quickstart-publish-iis.png "Vyberte IIS, FTP atd.")

1. Jako metodu nasazení vyberte **nasazení webu** . Nasazení webu zjednodušuje nasazení webových aplikací a webů na servery služby IIS a musí být nainstalováno jako aplikace na serveru. Pomocí [instalačního programu webové platformy](https://www.microsoft.com/web/downloads/platform.aspx) ho nainstalujte.

    ![Zvolit metodu nasazení](../deployment/media/quickstart-publish-iis-web-deploy.png "Vyberte IIS, FTP atd.")

1. Nakonfigurujte požadovaná nastavení pro metodu publikovat a vyberte **Dokončit**. 

    ![Podrobnosti o Nasazení webu připojení](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Pro publikování vyberte na stránce Souhrn možnost **publikovat** . V okně výstup se zobrazuje průběh a výsledky nasazení.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování. Profil publikování můžete také nakonfigurovat importem nastavení publikování.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do služby IIS](tutorial-import-publish-settings-iis.md)

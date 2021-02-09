---
title: Publikování na webu
description: Naučte se používat nástroj publikovat k publikování aplikací ASP.NET, ASP.NET Core, .NET Core a Pythonu na web ze sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf4248b9155e780b63faf48983adfca866440b98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927415"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikování webové aplikace na webu pomocí sady Visual Studio

Pomocí nástroje **publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python na web ze sady Visual Studio. Pro Node.js se tyto kroky podporují, ale uživatelské rozhraní se liší.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci pro Windows do síťové sdílené složky, přečtěte si téma [nasazení desktopové aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLR naleznete informace v tématu [nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo pro C/C++ viz [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikování na webu

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte   >  položku nabídky **publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Vyberte možnost pro **novou** položku.

1. V okně **publikovat** vyberte možnost **webový server (IIS)**.

    ![Zvolit cíl publikování](../deployment/media/quickstart-publish-iis.png "Vyberte IIS, FTP atd.")

1. Jako metodu nasazení vyberte **nasazení webu** . Nasazení webu zjednodušuje nasazení webových aplikací a webů na servery služby IIS a musí být nainstalováno jako aplikace na serveru. Pomocí [instalačního programu webové platformy](https://www.microsoft.com/web/downloads/platform.aspx) ho nainstalujte.

    ![Zvolit metodu nasazení](../deployment/media/quickstart-publish-iis-web-deploy.png "Vyberte IIS, FTP atd.")

1. Nakonfigurujte požadovaná nastavení pro metodu publikovat a vyberte **Dokončit**. 

    ![Podrobnosti o Nasazení webu připojení](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Pro publikování vyberte na stránce Souhrn možnost **publikovat** . V okně výstup se zobrazuje průběh a výsledky nasazení.

   Pokud potřebujete pomoc při řešení potíží ASP.NET Core ve službě IIS, přečtěte si téma [řešení potíží ASP.NET Core na Azure App Service a IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování. Profil publikování můžete také nakonfigurovat importem nastavení publikování.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do služby IIS](tutorial-import-publish-settings-iis.md)

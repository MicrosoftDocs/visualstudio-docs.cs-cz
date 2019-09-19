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
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127937"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikování webové aplikace na webu pomocí sady Visual Studio

Pomocí nástroje **publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python na web ze sady Visual Studio. Pro Node. js je postup podporován, ale uživatelské rozhraní je jiné.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci pro Windows do síťové sdílené složky, přečtěte si téma [nasazení desktopové aplikace pomocí](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) technologieC# ClickOnce (nebo Visual Basic). V C++případě/CLI si přečtěte téma [nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo pro CC++/, viz [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikování na webu

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte položku nabídky**publikovat** **sestavení** > ).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Vyberte **vytvořit nový profil**.

1. V dialogovém okně **vybrat cíl publikování** zvolte možnost **IIS, FTP atd**.

    ![Vyberte IIS, FTP atd.](../deployment/media/quickstart-publish-iis-ftp.png "Vyberte IIS, FTP atd.")

1. Vyberte **Publikovat**. Otevře se dialogové okno nastavení publikování profilu.

    ![Zvolit složku](../deployment/media/quickstart-publish-settings-web.png "Zvolit složku")

1. V poli **publikovat metodu** vyberte metodu, například **nasazení webu** nebo **FTP**. Nastavení, které vidíte dál, odpovídá vaší metodě publikování. Nasazení webu zjednodušuje nasazení webových aplikací a webů na servery služby IIS a musí být nainstalováno jako aplikace na serveru. Pomocí [instalačního programu webové platformy](https://www.microsoft.com/web/downloads/platform.aspx) ho nainstalujte.

1. Nakonfigurujte požadovaná nastavení pro metodu publikování a vyberte **ověřit připojení**. Pokud je server nebo cíl k dispozici a je správné nastavení, zobrazí se zpráva s oznámením o připojení a Vy jste připraveni publikovat.

    ![Ověření připojení](../deployment/media/quickstart-publish-web-deploy.png "Ověření připojení")

1. Vyberte **Nastavení** a nakonfigurujte další nastavení nasazení, například zda nasadit konfiguraci ladění nebo vydání, a pak vyberte **Uložit**. Pokud provádíte ladění vzdáleně, je vyžadována konfigurace ladění.

1. Pro publikování vyberte **publikovat**. V okně výstup se zobrazuje průběh a výsledky nasazení.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste zjistili, jak pomocí sady Visual Studio vytvořit profil publikování. Profil publikování můžete také nakonfigurovat importem nastavení publikování.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do služby IIS](tutorial-import-publish-settings-iis.md)

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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127937"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikování webové aplikace na web pomocí Visual Studia

Pomocí nástroje **Publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Jádra, .NET Core a Pythonu na web z Visual Studia. Pro Node.js jsou podporovány kroky, ale uživatelské rozhraní se liší.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci windows do sdílené síťové složky, přečtěte si část [Nasazení aplikace klasické pracovní plochy pomocí clickonce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLI [najdete v tématu Nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo v případě C/C++ najdete v [tématu Nasazení nativní aplikace pomocí instalačního projektu](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publikovat na webu

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat** (nebo použijte položku nabídky**Publikovat** **sestavení).** > 

    ![Příkaz Publikovat v kontextové nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "Zvolte Publikovat")

1. Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat.** Vyberte **Vytvořit nový profil**.

1. V **dialogovém** okně Vybrat cíl publikování zvolte **Službu IIS, FTP atd**.

    ![Zvolte IIS, FTP atd.](../deployment/media/quickstart-publish-iis-ftp.png "Zvolte IIS, FTP atd.")

1. Vyberte **Publikovat**. Otevře se dialogové okno Nastavení publikování profilu.

    ![Zvolte složku](../deployment/media/quickstart-publish-settings-web.png "Zvolte složku")

1. V poli **Metoda publikování** zvolte metodu, například **Nasazení webu** nebo **FTP**. Nastavení, která se zobrazí dále odpovídají vaší metodě publikování. Nasazení webu zjednodušuje nasazení webových aplikací a webových serverů na servery služby IIS a musí být nainstalováno jako aplikace na serveru. K instalaci použijte [instalační program webové platformy.](https://www.microsoft.com/web/downloads/platform.aspx)

1. Nakonfigurujte požadovaná nastavení metody publikování a vyberte **možnost Ověřit připojení**. Pokud je server nebo cíl k dispozici a nastavení jsou správná, zobrazí se zpráva, která označuje, že připojení je ověřeno a jste připraveni k publikování.

    ![Ověření připojení](../deployment/media/quickstart-publish-web-deploy.png "Ověření připojení")

1. Vyberte **Nastavení,** chcete-li nakonfigurovat další nastavení nasazení, například zda se má nasadit konfigurace ladění nebo vydání, a pak vyberte **Uložit**. Pokud ladíte vzdáleně, je vyžadována konfigurace ladění.

1. Chcete-li publikovat, vyberte **publikovat**. Okno Výstup zobrazuje průběh nasazení a výsledky.

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste se naučili, jak pomocí sady Visual Studio vytvořit profil publikování. Profil publikování můžete také nakonfigurovat importem nastavení publikování.

> [!div class="nextstepaction"]
> [Import nastavení publikování a nasazení do služby IIS](tutorial-import-publish-settings-iis.md)

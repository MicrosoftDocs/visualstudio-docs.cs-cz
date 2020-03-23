---
title: Nasazení do místní složky
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 862310c8c763ce366798bfacd4f4759d606bb33c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128208"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Nasazení aplikace do místní složky pomocí Sady Visual Studio

Pomocí nástroje **Publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python do místní složky z Visual Studia. Pro Node.js jsou podporovány kroky, ale uživatelské rozhraní se liší.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci windows do místní složky, [přečtěte si informace o nasazení aplikace klasické pracovní plochy pomocí clickonce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLI [najdete v tématu Nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo v případě C/C++ najdete v [tématu Nasazení nativní aplikace pomocí instalačního projektu](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Nasazení do místní složky

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat** (nebo použijte položku nabídky**Publikovat** **sestavení).** > 

    ![Příkaz Publikovat v kontextové nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "Zvolte Publikovat")

1. Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat.** Vyberte **Vytvořit nový profil**.

1. V **dialogovém** okně Vybrat cíl publikování zvolte **Složka**.

    ![Výběr místní složky jako cíle publikování](../deployment/media/quickstart-publish-folder.png "Zvolte složku")

1. Zadejte cestu nebo vyberte **Procházet** a určete místní složku.

1. Vyberte **Publikovat**. Visual Studio vytvoří projekt a publikuje jej do zadané složky. Zobrazí se podokno **Publikovat** vlastnosti projektu se souhrnem profilu.

    ![Podokno vlastností publikování se souhrnem profilu](../deployment/media/quickstart-publish-folder-summary.png)

1. Chcete-li konfigurovat nastavení nasazení, **vyberte** konfigurovat v souhrnu profilu a vyberte kartu **Nastavení.**

    ![Nastavení profilu](../deployment/media/quickstart-profile-settings.png "Nastavení profilu")

1. Nakonfigurujte možnosti, například zda chcete nasadit konfiguraci ladění nebo vydání, a pak vyberte **Uložit**.

1. Chcete-li znovu publikovat, vyberte **Publikovat**.

Nasadit publikované soubory jakýmkoli způsobem se vám líbí. Můžete je například zabalit do souboru *ZIP,* použít jednoduchý příkaz kopírování nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

## <a name="next-steps"></a>Další kroky

- [Nasazení aplikace .NET Core pomocí nástroje Publish](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Balíček desktopové aplikace pro Microsoft Store (přemostění na desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Nasazení rozhraní .NET Framework a aplikací](/dotnet/framework/deployment/)

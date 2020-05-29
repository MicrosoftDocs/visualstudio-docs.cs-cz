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
ms.openlocfilehash: 3355636eba7556a472d8ce272437fb07c30714be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184155"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Nasazení aplikace do místní složky pomocí sady Visual Studio

Pomocí nástroje **publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python do místní složky ze sady Visual Studio. Pro Node. js je postup podporován, ale uživatelské rozhraní je jiné.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci pro Windows do místní složky, přečtěte si téma [nasazení desktopové aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLR naleznete informace v tématu [nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo pro C/C++ viz [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Nasazení do místní složky

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky**publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. V dialogovém okně **publikovat** vyberte **Složka**.

    ![Zvolit složku jako cíl publikování](../deployment/media/quickstart-publish-folder.png "Zvolit složku")

1. Zadejte cestu nebo vyberte **Procházet** a zadejte složku.

    ![Zadejte cestu ke složce.](../deployment/media/quickstart-publish-folder-path.png "Zvolit složku")

1. Vyberte **Publikovat**. Visual Studio vytvoří projekt a publikuje ho do určené složky. Zobrazí se podokno **publikování** vlastností projektu, které zobrazuje souhrn profilu.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-folder-summary.png)

1. Chcete-li nakonfigurovat nastavení nasazení, vyberte možnost **Upravit** v souhrnu profilu publikování a vyberte kartu **Nastavení** .

    ![Nastavení profilu](../deployment/media/quickstart-profile-settings.png "Nastavení profilu")

1. Nakonfigurujte možnosti, jako je například, zda se má nasadit konfigurace ladění nebo vydání, a pak vyberte **Uložit**.

1. Pro opětovné publikování vyberte **publikovat**.

Nasaďte publikované soubory jakýmkoli způsobem. Můžete je například zabalit do souboru *. zip* , použít jednoduchý příkaz pro kopírování nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

## <a name="next-steps"></a>Další kroky

- [Nasazení aplikace .NET Core pomocí nástroje Publikovat](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Balíček desktopové aplikace pro Microsoft Store (přemostění na desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- Platformy [Nasazení .NET Framework a aplikací](/dotnet/framework/deployment/)

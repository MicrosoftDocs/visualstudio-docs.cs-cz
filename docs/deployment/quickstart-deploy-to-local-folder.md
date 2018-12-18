---
title: Nasazení do místní složky
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781910"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Nasazení aplikace do místní složky pomocí sady Visual Studio

Můžete použít **publikovat** nástroj pro publikování aplikace ASP.NET, ASP.NET Core, .NET Core a Pythonu do místní složky ze sady Visual Studio. Pro Node.js kroky jsou podporované, ale uživatelské rozhraní se liší.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Nasazení do místní složky

1. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **publikovat** (nebo použijte **sestavení** > **publikovat** položky nabídky).

    ![Příkaz Publikovat v místní nabídce projektu v Průzkumníku řešení](../deployment/media/quickstart-publish.png "tlačítko Publikovat")

1. Pokud jste dříve nakonfigurovali všech profilů publikování **publikovat** otevře se podokno. Vyberte **vytvořit nový profil**.

1. V **vyberte cíl publikování** dialogového okna zvolte **složky**.

    ![Zvolte místní složku jako publikovat nějaký](../deployment/media/quickstart-publish-folder.png "vybrat složku")

1. Zadejte cestu nebo vyberte **Procházet** určit místní složku.

1. Vyberte **publikovat**. Visual Studio vytvoří projekt a publikuje ji do zadané složky. Vlastnosti projektu **publikovat** otevře se podokno, zobrazuje profil souhrnu.

    ![Podokno vlastností zobrazuje souhrn profil publikování](../deployment/media/quickstart-publish-folder-summary.png)

1. Chcete-li konfigurovat nastavení nasazení, vyberte **konfigurovat** v profilu summary a vyberte **nastavení** kartu.

    ![Nastavení profilu](../deployment/media/quickstart-profile-settings.png "nastavení profilu")

1. Konfigurovat možnosti, jako například, jestli se má nasadit konfigurace ladění nebo uvolnění a pak vyberte **Uložit**.

1. Chcete-li znovu publikovat, vyberte **publikovat**.

Nasaďte publikované soubory žádným způsobem, který vám vyhovuje. Například je do balíčku *ZIP* souboru, použijte příkaz jednoduché kopírování nebo nasazení v balíčcích instalace podle vašeho výběru.

## <a name="next-steps"></a>Další kroky

- [Nasazení aplikace .NET Core pomocí nástroje Publish](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Balíček desktopové aplikace pro Microsoft Store (přemostění na desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Nasazení rozhraní .NET Framework a aplikace](/dotnet/framework/deployment/)

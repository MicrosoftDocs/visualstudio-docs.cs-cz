---
title: Nasazení do místní složky
description: Naučte se, jak pomocí nástroje Publikovat publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python do složky ze sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f392cc2dcb474487a37076229c0b10f7359b9251
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349565"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Nasazení aplikace do složky pomocí sady Visual Studio

Pomocí nástroje **publikovat** můžete publikovat aplikace ASP.NET, ASP.NET Core, .NET Core a Python do složky ze sady Visual Studio. Pro Node.js se tyto kroky podporují, ale uživatelské rozhraní se liší.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Pokud potřebujete publikovat desktopovou aplikaci pro Windows do složky, přečtěte si téma [nasazení desktopové aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic). V jazyce C++/CLR naleznete informace v tématu [nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo pro C/C++ viz [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Nasazení do místní složky

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky **publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-publish.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, zobrazí se okno **publikovat** . Vyberte možnost pro **novou** položku.

1. V okně **publikovat** vyberte **Složka**.

    ![Zvolit složku jako cíl publikování](../deployment/media/quickstart-publish-folder-new.png "Zvolit složku")

1. Zadejte cestu nebo vyberte **Procházet** a zadejte složku.

    ![Zadejte cestu ke složce.](../deployment/media/quickstart-publish-folder-path.png "Zvolit složku")

1. Vyberte **Publikovat**. Visual Studio vytvoří projekt a publikuje ho do určené složky. Zobrazí se podokno **publikování** vlastností projektu, které zobrazuje souhrn profilu.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-publish-folder-summary.png)

1. Chcete-li nakonfigurovat nastavení nasazení, vyberte možnost **Upravit** v souhrnu profilu publikování a vyberte kartu **Nastavení** .

   Nastavení, která vidíte, závisí na typu vaší aplikace. Následující ilustrace ukazuje příklad nastavení aplikace ASP.NET Core.

    ![Nastavení profilu](../deployment/media/quickstart-profile-settings.png "Nastavení profilu")

    Další nápovědu k výběru nastavení v rozhraní .NET najdete v následujících tématech:

    - [Nasazení závislé na rozhraní vs. samostatně uzavřené nasazení](/dotnet/core/deploying/)
    - [Cílové identifikátory modulu runtime (přenosná RID, et al)](/dotnet/core/rid-catalog)
    - [Konfigurace ladění a vydaných verzí](../ide/understanding-build-configurations.md)

1. Nakonfigurujte možnosti, jako je například, zda se má nasadit konfigurace ladění nebo vydání, a pak vyberte **Uložit**.

1. Pro opětovné publikování vyberte **publikovat**.

Nasaďte publikované soubory jakýmkoli způsobem. Můžete je například zabalit do souboru *. zip* , použít jednoduchý příkaz pro kopírování nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

## <a name="next-steps"></a>Další kroky

Pro aplikace .NET:

- [Nasazení aplikace .NET Core pomocí nástroje Publikovat](/dotnet/core/deploying/deploy-with-vs)
- [Publikování aplikace .NET Core (nasazení závislá na rozhraní vs. samostatně zahrnutá nasazení)](/dotnet/core/deploying/)
- [Nasazení .NET Framework a aplikací](/dotnet/framework/deployment/)

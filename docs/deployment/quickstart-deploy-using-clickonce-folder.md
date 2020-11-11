---
title: Nasazení desktopové aplikace Windows .NET pomocí technologie ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: f2d7b500caacf320df599843e45cc4e93b4f3e69
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441302"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Nasazení desktopové aplikace Windows .NET pomocí technologie ClickOnce

Počínaje verzí Visual Studio 2019 verze 16,8 můžete použít nástroj **publikovat** k publikování aplikace .net Core 3,1 nebo novějších aplikací klasické pracovní plochy systému Windows pomocí technologie ClickOnce ze sady Visual Studio.

> [!NOTE]
> Pokud potřebujete publikovat .NET Framework aplikace systému Windows, přečtěte si téma [nasazení desktopové aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# nebo Visual Basic).

## <a name="publishing-with-clickonce"></a>Publikování pomocí technologie ClickOnce

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat** (nebo použijte **Build**  >  položku nabídky **publikovat** sestavení).

    ![Příkaz publikovat v místní nabídce projektu v Průzkumník řešení](../deployment/media/quickstart-clickonce-solution-explorer.png "Zvolit publikování")

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, zobrazí se stránka **publikování** . Vyberte možnost pro **novou** položku.

1. V průvodci **publikováním** vyberte **Složka**.

    ![Zvolit složku jako cíl publikování](../deployment/media/quickstart-clickonce-publish-folder-category.png "Zvolit složku")

1. Na stránce **konkrétní cíl** vyberte možnost **ClickOnce**.

    ![Vybrat ClickOnce jako konkrétní cíl](../deployment/media/quickstart-clickonce-publish-folder-target.png "Zvolit ClickOnce")

1. Zadejte cestu nebo vyberte **Procházet** a vyberte umístění pro publikování.

    ![Zadejte cestu k umístění pro publikování.](../deployment/media/quickstart-clickonce-publish-location.png "Zadejte cestu.")

1. Na stránce **umístění instalace** vyberte, odkud budou uživatelé instalovat aplikaci.

    ![Zadejte cestu ke složce.](../deployment/media/quickstart-clickonce-install-location.png "Zvolit umístění instalace")

1. Na stránce **Nastavení** můžete zadat nastavení potřebná pro ClickOnce.

1. Pokud jste vybrali instalaci z cesty UNC nebo webu, Tato stránka vám umožní určit, jestli je aplikace k dispozici offline. Pokud je tato možnost vybrána, tato možnost zobrazí aplikaci v nabídce Start a uživatel umožní, aby se aplikace automaticky aktualizovala při publikování nové verze. Ve výchozím nastavení jsou aktualizace k dispozici v umístění instalace.  Pokud chcete mít k dispozici jiné umístění pro aktualizace, můžete ji zadat pomocí odkazu aktualizovat nastavení. Pokud nechcete, aby byla aplikace k dispozici v režimu offline, bude spuštěna z umístění instalace.

    ![Zadat nastavení publikování](../deployment/media/quickstart-clickonce-unc-settings.png "Zvolit nastavení publikování")

1. Pokud jste zvolili instalaci z disku CD, DVD nebo USB, Tato stránka vám také umožní určit, jestli aplikace podporuje automatické aktualizace. Pokud se rozhodnete pro podporu aktualizací, vyžaduje se umístění aktualizace a musí se jednat o platnou cestu UNC nebo Web.

    ![Zvolit nastavení publikování](../deployment/media/quickstart-clickonce-settings.png "Zvolit nastavení publikování")

Součástí této stránky je možnost určit, které **soubory aplikace** se mají zahrnout do nastavení, které **požadavky** na instalaci balíčků nainstalovat a další **Možnosti** prostřednictvím odkazů v horní části stránky.

Na této stránce také můžete nastavit verzi publikování a pokud se bude verze automaticky zvyšovat při každém publikování.

> [!NOTE]
> Číslo verze publikování je pro každý profil ClickOnce jedinečné. Pokud plánujete, že máte více než jeden profil, budete si muset na to pamatovat.

10. Na stránce **podepsat manifesty** můžete určit, zda mají být manifesty podepsány a které certifikát použít.

    ![Podepisování manifestů ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Na stránce **Konfigurace** můžete vybrat požadovanou konfiguraci projektu.

     ![Zadat konfiguraci publikování](../deployment/media/quickstart-clickonce-configuration.png)

    Další nápovědu k výběru nastavení najdete v následujících tématech:

    - [Nasazení závislé na rozhraní vs. samostatně uzavřené nasazení](/dotnet/core/deploying/)
    - [Cílové identifikátory modulu runtime (přenosná RID, et al)](/dotnet/core/rid-catalog)
    - [Konfigurace ladění a vydaných verzí](../ide/understanding-build-configurations.md)

1. Vyberte **Dokončit** a uložte nový publikační profil ClickOnce.

1. Na stránce **Souhrn** vyberte **publikovat** a aplikace Visual Studio sestaví projekt a publikuje ho do zadané složky pro publikování. Na této stránce se zobrazuje také souhrn profilu.

    ![Podokno vlastností publikování znázorňující souhrn profilu](../deployment/media/quickstart-clickonce-summary.png)

1. Pro opětovné publikování vyberte **publikovat**.

## <a name="next-steps"></a>Další kroky

Pro aplikace .NET:

- [Nasazení .NET Framework a aplikací](/dotnet/framework/deployment/)
- [Odkaz na ClickOnce](clickonce-reference.md)

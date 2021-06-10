---
title: Zahrnout požadavky (aplikace ClickOnce)
description: Zjistěte, jak získat instalační balíčky pro požadované součásti pro distribuci aplikace ClickOnce pro vývojový počítač.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877738"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Postupy: Zahrnutí požadavků do aplikace ClickOnce
Než budete moci distribuovat požadovaný software s aplikací, musíte nejdřív stáhnout instalační balíčky pro tyto požadavky [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do vývojového počítače. Když publikujete aplikaci a zvolíte Stáhnout požadavky ze stejného umístění jako moje **aplikace,** dojde k chybě, pokud instalační balíčky nejsou ve složce **Packages.**

> [!NOTE]
> Pokud chcete přidat instalační balíček pro .NET Framework, podívejte se [.NET Framework Průvodce nasazením pro vývojáře.](/dotnet/framework/deployment/deployment-guide-for-developers)

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Přidání instalačního balíčku pomocí Package.xml

1. V Průzkumník souborů otevřete složku **Packages** (Balíčky).

    Ve výchozím nastavení je cesta `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

>[!NOTE]
> Počínaje verzí Visual Studio 2019 s aktualizací Update 7 budou zjištěny také balíčky bootstrapperu v cestě *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

2. Otevřete složku požadované součásti, kterou chcete přidat, a pak otevřete složku jazyka pro nainstalovanou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje (například **en** pro angličtinu).

3. V Poznámkovém bloku otevřete *souborPackage.xml.*

4. Vyhledejte **element Name,** který obsahuje `http://go.microsoft.com/fwlink` , a zkopírujte adresu URL. Zahrřte **část LinkID** .)

   > [!NOTE]
   > Pokud žádný **element Name** neobsahuje , otevřeteProduct.xmlv kořenové složce požadované součásti a `http://go.microsoft.com/fwlink` vyhledejte řetězec **fwlink.** 

   > [!IMPORTANT]
   > Některé požadované softwarové programy mohou mít několik instalačních balíčků (například v 32bitových nebo 64bitových systémech). Pokud více **elementů** Název **obsahuje fwlink**, je nutné zbývající kroky opakovat pro každý z nich.

5. Vložte adresu URL do adresního řádku prohlížeče a po zobrazení výzvy ke spuštění nebo uložení zvolte **Uložit.**

    Tento krok stáhne instalační soubor do počítače.

6. Zkopírujte soubor do kořenové složky požadovaného softwaru.

    Například pro požadovaný .NET Framework 4.7.2 zkopírujte soubor do složky *\Packages\DotNetFX472.*

    Nyní můžete instalační balíček distribuovat spolu s aplikací.

## <a name="see-also"></a>Viz také
- [Postupy: Instalace požadavků pomocí aplikace ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)

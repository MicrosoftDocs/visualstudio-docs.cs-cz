---
title: Zahrnutí balíčku NuGet do projektu
description: Tento dokument popisuje, jak zahrnout balíček NuGet v projektu pomocí Visual Studio pro Mac. Prochází hledáním a stahováním balíčku a také zavedením integračních funkcí ide.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127241"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalace a správa balíčků NuGet v Sadě Visual Studio pro Mac

NuGet Package Manager UI v Sadě Visual Studio pro Mac umožňuje snadno nainstalovat, odinstalovat a aktualizovat balíčky NuGet v projektech a řešeních. Můžete vyhledávat a přidávat balíčky do vašich projektů .NET Core, ASP.NET Core a Xamarin.

Tento článek popisuje, jak zahrnout balíček NuGet v projektu a ukazuje řetězec nástrojů, který umožňuje proces bezproblémový.

Úvod k používání NuGetu ve Visual Studiu for Mac najdete v [tématu Úvodní příručka: Instalace a použití balíčku ve Visual Studiu for Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Vyhledání a instalace balíčku

1. S projektem otevřeným v Sadě Visual Studio pro Mac klikněte pravým tlačítkem myši na složku **Závislosti** **(Složka Balíčky,** pokud používáte projekt Xamarin) v **panelu řešení** a vyberte **Spravovat balíčky NuGet...**.

    ![Přidat novou akci kontextu balíčku NuGet](media/nuget-walkthrough-packages-menu.png)

2. To spustí **okno Spravovat nugetové balíčky.** Ujistěte se, že zdroj rozevírací v levém `nuget.org`horním rohu dialogového okna je nastavena na , takže prohledáváte centrální úložiště balíčků NuGet.

    ![Seznam nugetových balíčků](media/nuget-walkthrough-add-packages1.png)

3. Pomocí vyhledávacího pole v pravém horním rohu vyhledejte `EntityFramework`konkrétní balíček, například . Pokud jste našli balíček, který chcete použít, vyberte jej a klepnutím na tlačítko **Přidat balíček** zahájíte instalaci.

    ![Přidat balíček EntityFramework NuGet](media/nuget-walkthrough-add-packages2.png)

4. Jakmile je balíček stažen, bude přidán do vašeho projektu. Řešení se změní v závislosti na typu projektu, který upravujete:

    **Projekty Xamarin**
    * Uzel **Reference** bude obsahovat seznam všech sestavení, které jsou součástí balíčku NuGet.
    * Uzel **Balíčky** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.
    
    **Základní projekty .NET**

    * **Závislosti > nugetuzlu** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.

## <a name="using-nuget-packages"></a>Použití balíčků NuGet

Po přidání balíčku NuGet a aktualizace odkazů na projekt můžete naprogramovat proti api stejně jako u libovolného odkazu na projekt.

Ujistěte se, `using` že přidáte všechny požadované direktivy do horní části souboru:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualizace balíčků

Aktualizace balíčků lze provést buď všechny najednou, kliknutím pravým tlačítkem myši na uzel **závislosti** **(Balíčky** uzel pro projekty Xamarin), nebo jednotlivě na každém balíčku. Když je k dispozici nová verze balíčku NuGet, zobrazí ![](media/nuget-walkthrough-update-icon.png)se ikona aktualizace šipka nahoru s kruhem .

Klikněte pravým tlačítkem myši na **závislosti** pro přístup k místní nabídce a zvolte **Aktualizovat** aktualizovat všechny balíčky:

![Nabídka Balíčky](media/nuget-walkthrough-packages-menu-update.png)

* **Spravovat balíčky NuGet** – otevře okno pro přidání dalších balíčků do projektu.
* **Aktualizace** - Zkontroluje zdrojový server pro každý balíček a stáhne všechny novější verze.
* **Obnovení** – Stáhne všechny chybějící balíčky (bez aktualizace existujících balíčků na novější verze).

Možnosti aktualizace a obnovení jsou také k dispozici na úrovni řešení a ovlivňují všechny projekty v řešení.

### <a name="locating-outdated-packages"></a>Vyhledání zastaralých balíčků
Na panelu řešení můžete zobrazit, jaká verze balíčku je aktuálně nainstalována, a kliknout pravým tlačítkem myši na balíček, který chcete aktualizovat.

![Nabídka Balíčky s možnostmi aktualizace, odebrání, aktualizace](media/nuget-walkthrough-PackageMenu.png)

Zobrazí se také oznámení vedle názvu balíčku, když je k dispozici nová verze balíčku, takže se můžete rozhodnout, zda jej budete chtít aktualizovat.

![Oznámení zobrazené, když je k dispozici nová verze balíčku](media/nuget-walkthrough-package-update-available.png)

V zobrazené nabídce máte dvě možnosti:

* **Update** - Zkontroluje zdrojový server a stáhne novější verzi (pokud existuje).
* **Odebrat** - Odebere balíček z tohoto projektu a odebere příslušná sestavení z odkazů projektu.

## <a name="manage-packages-for-the-solution"></a>Správa balíčků pro řešení

Správa balíčků pro řešení je pohodlným prostředkem pro práci s více projekty současně.

1. Klikněte pravým tlačítkem myši na řešení a vyberte **spravovat balíčky NuGet...**:

    ![Správa balíčků NuGet pro řešení](media/nuget-walkthrough-manage-packages-solution.png)

1. Při správě balíčků pro řešení umožňuje unové oi vybrat projekty, které jsou ovlivněny operacemi:

    ![Výběr projektu při správě balíčků pro řešení](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Karta Konsolidovat

Při práci v řešení s více projekty, je považováno za osvědčený postup, abyste se ujistili, že kdekoli použijete stejný balíček NuGet v každém projektu, používáte také stejný počet verzí tohoto balíčku. Visual Studio pro Mac pomáhá usnadnit tím, že poskytuje **kartu Konsolidovat** v uzdu Správce balíčků, když se rozhodnete spravovat balíčky pro řešení. Pomocí této karty můžete snadno zjistit, kde jsou balíčky s odlišnými čísly verzí používány různými projekty v řešení:

![Karta Konsolidovat ui správce balíčků](media/nuget-walkthrough-consolidate-tab.png)

V tomto příkladu projekt NuGetDemo používá Microsoft.EntityFrameworkCore 2.20, zatímco NuGetDemo.Shared používá Microsoft.EntityFrameworkCore 2.2.6. Chcete-li konsolidovat verze balíčku, postupujte takto:

- Vyberte projekty, které chcete aktualizovat v seznamu projektů.
- Vyberte verzi, která se má použít ve všech těchto projektech v seznamu **Nová verze,** například Microsoft.EntityFrameworkCore 3.0.0.
- Vyberte tlačítko **Konsolidovat balíček.**

Správce balíčků nainstaluje vybranou verzi balíčku do všech vybraných projektů, po kterých se balíček již nezobrazí na kartě **Konsolidovat.**

## <a name="adding-package-sources"></a>Přidání zdrojů balíčků

Balíčky, které jsou k dispozici pro instalaci, jsou zpočátku načteny z nuget.org. Do Visual Studia for Mac však můžete přidat další umístění balíčků. To může být užitečné pro testování vlastní chod nuget balíčky ve vývoji nebo použít soukromý server NuGet uvnitř vaší společnosti nebo organizace.

V Sadě Visual Studio pro Mac přejděte do **předvoleb > sady Visual Studio > NuGet > zdroje** a zobrazte a upravte seznam zdrojů balíčků. Všimněte si, že zdroje mů e být vzdálený server (určený adresou URL) nebo místní adresář.

![Zdroje balíčků](media/nuget-walkthrough-PackageSource.png)

Kliknutím na **Přidat** nastavte nový zdroj. Zadejte popisný název a adresu URL (nebo cestu k souboru) ke zdroji balíčku. Pokud je zdrojem zabezpečený webový server, zadejte také uživatelské jméno a heslo, jinak ponechte tyto položky prázdné:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource2.png)

Při hledání balíčků lze vybrat různé zdroje:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Správa verzí

Dokumentace NuGet popisuje [pomocí NuGet bez potvrzení balíčků do správy zdrojového kódu](/nuget/consume-packages/packages-and-source-control). Pokud nechcete ukládat binární soubory a nepoužívané informace do správy zdrojového kódu, můžete nakonfigurovat Visual Studio pro Mac tak, aby automaticky obnovovala balíčky ze serveru. To znamená, že když vývojář načte projekt ze správy zdrojového kódu poprvé, Visual Studio pro Mac automaticky stáhne a nainstaluje požadované balíčky.

![Automatické obnovení balíčků](media/nuget-walkthrough-AutoRestore.png)

Podrobnosti o tom, jak vyloučit `packages` sledovaný adresář, naleznete v konkrétní dokumentaci správy zdrojového kódu.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Viz také

* [Instalace a použití balíčku v sadě Visual Studio (ve Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

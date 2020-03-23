---
title: Zahrnutí balíčku NuGet do projektu
description: Tento dokument popisuje, jak zahrnout balíček NuGet v projektu Xamarin. Prochází hledáním a stahováním balíčku a také zavedením integračních funkcí ide.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.openlocfilehash: 728a225f4a1d14af986039cae7cb2fc8a493ecc9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983301"
---
# <a name="include-a-nuget-package-in-your-project"></a>Zahrnutí balíčku NuGet do projektu

NuGet je nejoblíbenější správce balíčků pro vývoj rozhraní .NET a je integrován do sady Visual Studio pro Mac a Visual Studio v systému Windows. Můžete vyhledávat a přidávat balíčky do projektů Xamarin.iOS a Xamarin.Android pomocí ide.

Tento článek popisuje, jak zahrnout balíček NuGet v projektu a ukazuje řetězec nástrojů, který umožňuje proces bezproblémový.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet ve Visual Studiu pro Mac

Chcete-li demonstrovat funkce balíčku NuGet, nejprve projdeme vytvoření majestátně a přidáme do ní balíček. Pak budeme diskutovat o funkcích IDE, které pomáhají spravovat balíčky.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Nejprve vytvořte `HelloNuget` projekt s názvem, jak je znázorněno níže. Tento příklad ukazuje šablonu aplikace pro jednotné zobrazení iOS, ale jakýkoli podporovaný typ projektu by fungoval:

![Vytvoření nového projektu iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Přidání balíčku

Když je projekt otevřený v Sadě Visual Studio for Mac, klikněte pravým tlačítkem myši na složku **Balíčky** na **panelu řešení** a vyberte **Přidat balíčky**:

![Přidat novou akci kontextu balíčku NuGet](media/nuget-walkthrough-PackagesMenu.png)

Tím se spustí okno **Přidat balíčky.** Ujistěte se, že zdroj rozevírací, je nastavena na `nuget.org`:

![Rozevírací seznam zdroje](media/nuget-walkthrough-Source.png)

Když se otevře okno načte seznam balíčků z výchozího zdroje balíčku: nuget.org. Počáteční výsledky vypadají takto:

![Seznam nugetových balíčků](media/nuget-walkthrough-AddPackages1.png)

Pomocí vyhledávacího pole v pravém horním rohu vyhledejte `azure`konkrétní balíček, například . Až najdete balíček, který chcete použít, vyberte ho a klepnutím na tlačítko **Přidat balíček** zahájíte instalaci.

[Přidat balíček Azure NuGet](media/nuget-walkthrough-AddPackages2.png)

Jakmile je balíček stažen, bude přidán do vašeho projektu. Řešení se změní takto:

* Uzel **Reference** bude obsahovat seznam všech sestavení, které jsou součástí balíčku NuGet.
* Uzel **Balíčky** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.
* Do projektu bude přidán soubor **packages.config.** Tento soubor XML používá rozhraní IDE ke sledování, na které verze balíčků se v tomto projektu odkazuje. Tento soubor by neměl být ručně upravován, ale měli byste jej uchovávat ve správě verzí. Všimněte si, že soubor project.json lze použít místo souboru packages.config. Soubor project.json je nový formát souboru balíčku představený s NuGet 3, který podporuje přenosné obnovení. Podrobnější informace o souboru project.json naleznete v [dokumentaci NuGet](/NuGet/Schema/Project-Json). Soubor project.json je třeba přidat ručně a projekt uzavřen a znovu otevřen před project.json soubor se používá v sadě Visual Studio for Mac.

## <a name="using-nuget-packages"></a>Použití balíčků NuGet

Po přidání balíčku NuGet a aktualizace odkazů na projekt můžete naprogramovat proti api stejně jako u libovolného odkazu na projekt.

Ujistěte se, `using` že přidáte všechny požadované direktivy do horní části souboru:

```csharp
using Newtonsoft.Json;
```

Většina NuGet poskytují další informace, jako je například readme nebo odkaz na stránku projektu nuget. Odkaz na to můžete obvykle najít v reklamě na balíček na stránce Přidat balíčky:

[Zobrazit odkaz na stránku projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aktualizace balíčků

Aktualizace balíčků lze provádět buď všechny najednou, kliknutím pravým tlačítkem myši na uzel **Balíčky** nebo jednotlivě na každé součásti.

Kliknutím pravým tlačítkem myši na **balíčky** zobrazíte kontextovou nabídku:

![Nabídka Balíčky](media/nuget-walkthrough-PackagesMenu.png)

* **Přidat balíčky** - Otevře okno pro přidání dalších balíčků do projektu.
* **Aktualizace** - Zkontroluje zdrojový server pro každý balíček a stáhne všechny novější verze.
* **Obnovení** – Stáhne všechny chybějící balíčky (bez aktualizace existujících balíčků na novější verze).

Možnosti aktualizace a obnovení jsou také k dispozici na úrovni řešení a ovlivňují všechny projekty v řešení.

Můžete také kliknout pravým tlačítkem myši na jednotlivé balíčky pro přístup k kontextové nabídce:

![Nabídka Balíčky](media/nuget-walkthrough-PackageMenu.png)

* **Číslo verze** - Číslo verze je zakázaná položka nabídky - je poskytována pouze pro informační účely.
* **Update** - Zkontroluje zdrojový server a stáhne novější verzi (pokud existuje).
* **Odebrat** - Odebere balíček z tohoto projektu a odebere příslušná sestavení z odkazů projektu.

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

---
title: Zahrnutí balíčku NuGet do projektu
description: Tento dokument popisuje postup zahrnutí balíčku NuGet do projektu Xamarin. Provede hledání a stahování balíčku, jakož i představení funkcí integrace integrovaného vývojového prostředí.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.openlocfilehash: 0a98425ba12ae7aba16a2bc6ffa29e701c1b9f11
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948619"
---
# <a name="include-a-nuget-package-in-your-project"></a>Zahrnutí balíčku NuGet do projektu

NuGet je nejoblíbenější Správce balíčků pro vývoj na platformě .NET a je součástí sady Visual Studio pro Mac a Visual Studio na Windows. Můžete vyhledat a přidat balíčky pro vaše projekty Xamarin.iOS a Xamarin.Android buď integrovaném vývojovém prostředí.

Tento článek popisuje, jak zahrnout do projektu balíček NuGet a ukazuje řetězce nástrojů, které zajišťuje bezproblémovou procesu.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet v sadě Visual Studio pro Mac

K předvedení funkčnosti balíčku NuGet, nejprve provedeme procesem vytvoření nové aplikace a přidání balíčku do něj. Potom probereme funkce integrovaného vývojového prostředí, které pomáhají spravovat balíčky.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Nejprve vytvořte projekt s názvem `HelloNuget` jak je znázorněno níže. Tento příklad ukazuje šablonu jediné zobrazení aplikace iOS, ale bude fungovat libovolným typem projektu podporované:

![Vytvoření nového projektu pro iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Přidání balíčku

V sadě Visual Studio pro Mac po otevření projektu klikněte pravým tlačítkem na **balíčky** složky **oblasti řešení** a vyberte **přidat balíčky**:

![Přidat novou akci kontextu balíček NuGet](media/nuget-walkthrough-PackagesMenu.png)

Tím se spustí **přidat balíčky** okna. Zkontrolujte, že zdroj rozevíracího seznamu, je nastavená na `nuget.org`:

![Seznam zdrojů rozevíracího seznamu](media/nuget-walkthrough-Source.png)

Po otevření okna načte seznam balíčků z výchozí zdroj balíčku: nuget.org. První výsledky vypadají takhle:

![Seznam balíčků NuGet](media/nuget-walkthrough-AddPackages1.png)

Pomocí vyhledávacího pole v pravém horním rohu k vyhledání konkrétního balíčku, například `azure`. Pokud nenajdete balíček, který chcete použít, vyberte ho a klikněte **přidat balíček** tlačítko a spusťte instalaci.

[Přidejte balíček NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Po stažení balíčku, přidá se do projektu. Řešení se změní takto:

* **Odkazy** uzlu bude obsahovat seznam všech sestavení, které jsou součástí balíčku NuGet.
* **Balíčky** uzel se zobrazí každý balíček NuGet, který jste si stáhli. Můžete aktualizovat nebo odebrat balíček z tohoto seznamu.
* A **souboru packages.config** soubor bude přidán do projektu. Tento soubor XML používá rozhraní IDE ke sledování verzí balíčku se odkazuje v tomto projektu. Tento soubor by neměl být ručně upravit, ale je nutné jej uschovat ho ve správě verzí. Všimněte si, že soubor project.json je možné použít místo souboru packages.config. Soubor project.json je nový formát souboru balíčku představeny s nástrojem NuGet 3, která podporuje tranzitivní obnovení. Podrobnější informace o souboru project.json najdete v [dokumentace pro NuGet](http://docs.microsoft.com/NuGet/Schema/Project-Json). Soubor project.json musí přidat ručně a projekt zavře a zase otevře před soubor project.json se používá v sadě Visual Studio pro Mac.

## <a name="using-nuget-packages"></a>Pomocí balíčků NuGet

Jakmile se přidal balíček NuGet a aktualizovat odkazy projektu, můžete programovat proti rozhraní API, jako by se všechny odkazy projektu.

Ujistěte se, že přidáte všechny požadované `using` příkazů horní části souboru:

```csharp
using Newtonsoft.Json;
```

Většina NuGet poskytují další informace, jako je například projekt nebo soubor README stránce odkaz na zdroj Nuget. Odkaz na to obvykle najdete v balíčku blurb na stránce Přidat balíčky:

[Odkaz projektu stránku zobrazení](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aktualizace balíčků

Aktualizace balíčků může provést buď všechny najednou, kliknutím pravým tlačítkem na **balíčky** uzlu, nebo jednotlivě pro jednotlivé komponenty.

Klikněte pravým tlačítkem na **balíčky** pro přístup k místní nabídky:

![Balíčky nabídky](media/nuget-walkthrough-PackagesMenu.png)

*   **Přidání balíčků** -otevře se okno pro přidání dalších balíčků do projektu.
*   **Aktualizace** – kontroluje zdrojový server pro každý balíček a stáhne všechny novější verze.
*   **Obnovení** – soubory ke stažení všechny chybějící balíčky (bez aktualizace existující balíčky na novější verze).

Aktualizace a možnosti obnovení jsou také k dispozici na úrovni řešení a vliv na všechny projekty v řešení.

Klikněte pravým tlačítkem můžete také na jednotlivé balíčky pro přístup k místní nabídka:

![Balíčky nabídky](media/nuget-walkthrough-PackageMenu.png)

*   **Číslo verze** – číslo verze se zakázanou položku nabídky – je určen pouze k informačním účelům.
*   **Aktualizace** – kontroluje zdrojového serveru a soubory ke stažení novější verze (pokud existuje).
*   **Odebrat** – odebere balíček z tohoto projektu a odstraní odpovídající sestavení z odkazů v projektu.

## <a name="adding-package-sources"></a>Přidání zdroje balíčků

Balíčky pro instalaci jsou zpočátku načíst z webu nuget.org. Však můžete přidat další umístění balíčku do sady Visual Studio for Mac. To může být užitečné pro testování vlastní balíčky NuGet ve vývoji, nebo použít privátní server NuGet uvnitř vaše společnost nebo organizace.

V sadě Visual Studio pro Mac, přejděte na **sady Visual Studio > Předvolby > NuGet > zdrojů** zobrazit a upravit seznam zdrojů balíčků. Všimněte si, že zdrojem může být vzdálený server (určené adresy URL) nebo do místního adresáře.

![Zdroje balíčků](media/nuget-walkthrough-PackageSource.png)

Klikněte na tlačítko **přidat** nastavit nový zdroj. Zadejte popisný název a URL (nebo cesta k souboru) ke zdroji balíčku. Pokud je zdroj zabezpečený webový server, zadejte uživatelské jméno a heslo, i, v opačném případě ponechte prázdné tyto položky:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource2.png)

Různé zdroje můžete pak vybrat při vyhledávání balíčků:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Správa verzí

Tento článek popisuje dokumentace pro NuGet [bez potvrzení balíčky do správy zdrojového kódu pomocí nástroje NuGet](/nuget/consume-packages/packages-and-source-control). Pokud nechcete ukládání binárních souborů a nepoužívané informace ve správě zdrojového kódu, můžete nakonfigurovat sady Visual Studio pro Mac, aby automaticky obnovit balíčky ze serveru. To znamená, že když vývojář poprvé načte projekt ze správy zdrojových kódů, Visual Studio for Mac automaticky stáhne a nainstaluje požadované balíčky.

![Automaticky obnovit balíčky](media/nuget-walkthrough-AutoRestore.png)

V dokumentaci konkrétní zdrojový ovládací prvek podrobné informace o tom, jak vyloučit `packages` z sledován.

## <a name="see-also"></a>Viz také:

* [Instalace a použití balíčku v sadě Visual Studio (ve Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

---
title: Zahrnutí balíčku NuGet do projektu
description: Tento dokument popisuje, jak zahrnout balíček NuGet do projektu Xamarin. Provede vás tím, že najde a stáhne balíček a také zavádí funkce integrace IDE.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 274e8defe25fa78c30aee72834e486b302a9af4e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729428"
---
# <a name="include-a-nuget-package-in-your-project"></a>Zahrnutí balíčku NuGet do projektu

NuGet je nejoblíbenější správce balíčků pro vývoj pro .NET a je integrovaný do Visual Studio pro Mac a sady Visual Studio ve Windows. Pomocí integrovaného vývojového prostředí (IDE) můžete v projektech Xamarin. iOS a Xamarin. Android vyhledat balíčky a přidat je do nich.

Tento článek popisuje, jak zahrnout balíček NuGet do projektu a demonstruje řetěz nástrojů, který tento proces způsobuje bez problémů.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet v Visual Studio pro Mac

Abychom předvedli funkci balíčku NuGet, nejprve si projdeme vytvořením nové aplikace a přidáním balíčku do ní. Pak se podíváme na funkce IDE, které vám pomůžou spravovat balíčky.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Nejprve vytvořte projekt s názvem, `HelloNuget` jak je znázorněno níže. Tento příklad ukazuje šablonu aplikace s jedním zobrazením pro iOS, ale všechny podporované typy projektu budou fungovat:

![Vytvořit nový projekt pro iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Přidání balíčku

Po otevření projektu v Visual Studio pro Mac klikněte pravým tlačítkem na složku **balíčky** v **oblast řešení** a vyberte **Přidat balíčky**:

![Akce kontextu přidání nového balíčku NuGet](media/nuget-walkthrough-PackagesMenu.png)

Tím se otevře okno **Přidat balíčky** . Zajistěte, aby byl zdrojový rozevírací seznam nastaven na hodnotu `nuget.org` :

![Rozevírací seznam zdrojového seznamu](media/nuget-walkthrough-Source.png)

Po otevření okna se načte seznam balíčků z výchozího zdroje balíčku: nuget.org. Počáteční výsledky vypadají takto:

![Výpis balíčků NuGet](media/nuget-walkthrough-AddPackages1.png)

Pomocí vyhledávacího pole v pravém horním rohu Najděte konkrétní balíček, například `azure` . Po nalezení balíčku, který chcete použít, ho vyberte a kliknutím na tlačítko **Přidat balíček** zahajte instalaci.

[Přidat balíček NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Po stažení balíčku se do projektu přidá. Řešení se změní následujícím způsobem:

* Uzel **odkazy** bude obsahovat seznam všech sestavení, která jsou součástí balíčku NuGet.
* Uzel **balíčky** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.
* Do projektu se přidá soubor **packages.config** . Tento soubor XML je používán rozhraním IDE ke sledování, které verze balíčku jsou odkazovány v tomto projektu. Tento soubor by neměl být upravován ručně, ale měli byste ho udržovat ve správě verzí. Všimněte si, že místo packages.config souboru se dá použít project.jsv souboru. project.jsv souboru je nový formát souboru balíčku, který je představený s NuGet 3, který podporuje přenosné obnovení. Podrobnější informace o project.jsnajdete v [dokumentaci k NuGet](/NuGet/Schema/Project-Json). project.jsv souboru je nutné přidat ručně a projekt se zavřel a znovu otevřel před tím, než se project.jsv souboru používá v Visual Studio pro Mac.

## <a name="using-nuget-packages"></a>Používání balíčků NuGet

Po přidání balíčku NuGet a aktualizace odkazů na projekt můžete programovat s rozhraními API stejně jako v případě jakýchkoli odkazů na projekt.

Ujistěte se, že jste `using` do horní části souboru přidali všechny požadované direktivy:

```csharp
using Newtonsoft.Json;
```

Většina NuGet poskytuje další informace, jako je například soubor READme nebo stránka projektu s odkazem na zdroj NuGet. Odkaz na tuto stránku můžete normálně najít v balíčku BLURB na stránce přidat balíčky:

[Zobrazit odkaz na stránku projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aktualizace balíčků

Aktualizace balíčků se dají provést najednou, a to tak, že pravým tlačítkem myši kliknete na uzel **balíčky** nebo na jednotlivé komponenty zvlášť.

Kliknutím pravým tlačítkem na **balíčky** získáte přístup k místní nabídce:

![Snímek obrazovky s vybraným uzlem balíčky a místní nabídka, která se otevře s příkazy pro přidání balíčků, aktualizace, obnovení a aktualizace.](media/nuget-walkthrough-PackagesMenu.png)

* **Přidat balíčky** – otevře okno pro přidání dalších balíčků do projektu.
* **Aktualizace** – zkontroluje zdrojový server pro každý balíček a stáhne všechny novější verze.
* **Obnovit** – stáhne všechny chybějící balíčky (bez aktualizace existujících balíčků na novější verze).

Možnosti aktualizace a obnovení jsou také k dispozici na úrovni řešení a mají vliv na všechny projekty v řešení.

Můžete také kliknout pravým tlačítkem na jednotlivé balíčky a získat přístup k místní nabídce:

![Snímek obrazovky s vybraným jednotlivými balíčky a místní nabídka, která se zobrazí po kliknutí pravým tlačítkem otevřít s příkazy pro aktualizace, odebrání a aktualizaci.](media/nuget-walkthrough-PackageMenu.png)

* **Číslo verze** – číslo verze je zakázaná položka nabídky – je k dispozici pouze pro informativní účely.
* **Aktualizace** – zkontroluje zdrojový server a stáhne novější verzi (pokud existuje).
* **Odebrat** – odebere balíček z tohoto projektu a odebere příslušná sestavení z odkazů projektu.

## <a name="adding-package-sources"></a>Přidávání zdrojů balíčků

Balíčky dostupné pro instalaci se zpočátku načítají z nuget.org. Do Visual Studio pro Mac však můžete přidat další umístění balíčků. To může být užitečné při testování vlastních balíčků NuGet ve vývoji nebo při používání privátního serveru NuGet v rámci vaší společnosti nebo organizace.

V Visual Studio pro Mac přejděte do části **Visual Studio > předvolby > > zdrojů NuGet** , abyste mohli zobrazit a upravit seznam zdrojů balíčků. Všimněte si, že zdrojem může být vzdálený server (určený adresou URL) nebo místní adresář.

![Zdroje balíčků](media/nuget-walkthrough-PackageSource.png)

Klikněte na tlačítko **Přidat** a nastavte nový zdroj. Zadejte popisný název a adresu URL (nebo cestu k souboru) do zdroje balíčku. Pokud je zdrojem zabezpečený webový server, zadejte taky uživatelské jméno a heslo. jinak ponechte prázdné tyto položky:

![Snímek obrazovky dialogového okna Přidat zdroj balíčku obsahující pole pro název, umístění, uživatelské jméno a heslo](media/nuget-walkthrough-PackageSource2.png)

Při hledání balíčků se pak dají vybrat různé zdroje:

![Snímek obrazovky přidat balíčky zobrazující rozevírací seznam zdrojů, které lze vybrat při hledání balíčků.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Správa verzí

Dokumentace k NuGet popisuje [použití NuGet bez potvrzení balíčků do správy zdrojových kódů](/nuget/consume-packages/packages-and-source-control). Pokud si nepřejete ukládat binární soubory a nepoužívané informace ve správě zdrojového kódu, můžete nakonfigurovat Visual Studio pro Mac pro automatické obnovení balíčků ze serveru. To znamená, že když vývojář poprvé načte projekt ze správy zdrojového kódu, Visual Studio pro Mac bude automaticky stahovat a instalovat požadované balíčky.

![Automaticky obnovit balíčky](media/nuget-walkthrough-AutoRestore.png)

Podrobnosti o tom, jak se má adresář vyřadit ze sledování, najdete v příslušné dokumentaci ke správě zdrojového kódu `packages` .

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Viz také

* [Instalace a použití balíčku v aplikaci Visual Studio (v systému Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

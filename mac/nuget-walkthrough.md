---
title: Zahrnutí balíčku NuGet do projektu
description: Tento dokument popisuje, jak zahrnout balíček NuGet do projektu pomocí Visual Studio pro Mac. Provede vás tím, že najde a stáhne balíček a také zavádí funkce integrace IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/17/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 22b2e07509403d8e19e3a3e920d45b064c2e51c0
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079479"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalace a Správa balíčků NuGet v Visual Studio pro Mac

Uživatelské rozhraní Správce balíčků NuGet v Visual Studio pro Mac umožňuje snadno nainstalovat, odinstalovat a aktualizovat balíčky NuGet v projektech a řešeních. Balíčky můžete vyhledat a přidat do projektů .NET Core, ASP.NET Core a Xamarin.

Tento článek popisuje, jak zahrnout balíček NuGet do projektu a demonstruje řetěz nástrojů, který tento proces způsobuje bez problémů.

Úvod k použití NuGet v Visual Studio pro Mac najdete v tématu [rychlý Start: Instalace a použití balíčku v Visual Studio pro Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Vyhledání a instalace balíčku

1. Otevřete-li projekt v Visual Studio pro Mac, klikněte pravým tlačítkem myši na složku **závislosti** (složka**balíčky** , pokud používáte projekt Xamarin) v **oblast řešení** a vyberte možnost **Přidat balíčky**.

    ![Akce kontextu přidání nového balíčku NuGet](media/nuget-walkthrough-PackagesMenu.png)

2. Tím se otevře okno **Přidat balíčky** . Zajistěte, aby se v levém horním rohu dialogu nastavila `nuget.org`zdrojová rozevírací seznam.

    ![Výpis balíčků NuGet](media/nuget-walkthrough-AddPackages1.png)

3. Pomocí vyhledávacího pole v pravém horním rohu Najděte konkrétní balíček, například `EntityFramework`. Po nalezení balíčku, který chcete použít, ho vyberte a kliknutím na tlačítko **Přidat balíček** zahajte instalaci.

    ![Přidat balíček NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

4. Po stažení balíčku se do projektu přidá. Řešení se změní v závislosti na typu projektu, který upravujete:

    **Projekty Xamarin**
    * Uzel **odkazy** bude obsahovat seznam všech sestavení, která jsou součástí balíčku NuGet.
    * Uzel **balíčky** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.
    
    **Projekty .NET Core**

    Uzel **nuget > Node NuGet** zobrazí každý balíček NuGet, který jste stáhli. Balíček můžete aktualizovat nebo odebrat z tohoto seznamu.

## <a name="using-nuget-packages"></a>Používání balíčků NuGet

Po přidání balíčku NuGet a aktualizace odkazů na projekt můžete programovat s rozhraními API stejně jako v případě jakýchkoli odkazů na projekt.

Ujistěte se, že jste do `using` horní části souboru přidali všechny požadované direktivy:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualizace balíčků

Aktualizace balíčků lze provést buď najednou, kliknutím pravým tlačítkem myši na uzel **závislosti** (nebo na uzlu **balíčky** pro projekty Xamarin) nebo jednotlivě na každé součásti.

Kliknutím pravým tlačítkem myši na **závislosti** přistupujete k místní nabídce:

![Nabídka balíčky](media/nuget-walkthrough-PackagesMenu.png)

* **Spravovat balíčky NuGet** – otevře okno pro přidání dalších balíčků do projektu.
* **Aktualizace** – zkontroluje zdrojový server pro každý balíček a stáhne všechny novější verze.
* **Obnovit** – stáhne všechny chybějící balíčky (bez aktualizace existujících balíčků na novější verze).

Možnosti aktualizace a obnovení jsou také k dispozici na úrovni řešení a mají vliv na všechny projekty v řešení.

Z panelu řešení můžete zobrazit aktuálně nainstalovanou verzi balíčku a kliknutím pravým tlačítkem na balíček aktualizovat.

![Nabídka balíčky s možnostmi aktualizace, odebrání a aktualizace](media/nuget-walkthrough-PackageMenu.png)

V případě, že je k dispozici nová verze balíčku, se zobrazí také oznámení vedle názvu balíčku, takže se můžete rozhodnout, jestli ho budete chtít aktualizovat.

![Oznámení zobrazené v případě, že je k dispozici nová verze balíčku](media/nuget-walkthrough-package-update-available.png)

V zobrazené nabídce máte dvě možnosti:

* **Aktualizace** – zkontroluje zdrojový server a stáhne novější verzi (pokud existuje).
* **Odebrat** – odebere balíček z tohoto projektu a odebere příslušná sestavení z odkazů projektu.

## <a name="adding-package-sources"></a>Přidávání zdrojů balíčků

Balíčky dostupné pro instalaci se zpočátku načítají z nuget.org. Do Visual Studio pro Mac však můžete přidat další umístění balíčků. To může být užitečné při testování vlastních balíčků NuGet ve vývoji nebo při používání privátního serveru NuGet v rámci vaší společnosti nebo organizace.

V Visual Studio pro Mac přejděte do části **Visual Studio > předvolby > > zdrojů NuGet** , abyste mohli zobrazit a upravit seznam zdrojů balíčků. Všimněte si, že zdrojem může být vzdálený server (určený adresou URL) nebo místní adresář.

![Zdroje balíčků](media/nuget-walkthrough-PackageSource.png)

Klikněte na tlačítko **Přidat** a nastavte nový zdroj. Zadejte popisný název a adresu URL (nebo cestu k souboru) do zdroje balíčku. Pokud je zdrojem zabezpečený webový server, zadejte taky uživatelské jméno a heslo. jinak ponechte prázdné tyto položky:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource2.png)

Při hledání balíčků se pak dají vybrat různé zdroje:

![Přidat zdroje balíčků](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Správa verzí

Dokumentace k NuGet popisuje [použití NuGet bez potvrzení balíčků do správy zdrojových kódů](/nuget/consume-packages/packages-and-source-control). Pokud si nepřejete ukládat binární soubory a nepoužívané informace ve správě zdrojového kódu, můžete nakonfigurovat Visual Studio pro Mac pro automatické obnovení balíčků ze serveru. To znamená, že když vývojář poprvé načte projekt ze správy zdrojového kódu, Visual Studio pro Mac bude automaticky stahovat a instalovat požadované balíčky.

![Automaticky obnovit balíčky](media/nuget-walkthrough-AutoRestore.png)

Podrobnosti o tom, jak se má `packages` adresář vyřadit ze sledování, najdete v příslušné dokumentaci ke správě zdrojového kódu.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Viz také:

* [Instalace a použití balíčku v aplikaci Visual Studio (v systému Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

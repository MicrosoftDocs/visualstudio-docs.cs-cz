---
title: Správa vlastností projektů a řešení
description: V tomto článku se dozvíte, jak spravovat vlastnosti projektů a řešení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985264"
---
# <a name="managing-project-and-solution-properties"></a>Správa vlastností projektů a řešení

## <a name="project-options"></a>Možnosti projektů

Možnosti projektu jsou specifické pro každý projekt a mají vliv na to, jak je projekt napsán, sestaven a spuštěn. To má na rozdíl od Visual Studio pro Mac předvolby (které nastaví možnosti specifické pro uživatele) a možnosti řešení (které nastaví možnosti pro celé řešení). Možnosti projektu jsou uloženy v souboru projektu (. csproj), aby ostatní vývojáři mohli správně sestavit a spustit projekt. S konkrétními možnostmi projektu může mnoho vývojářů pracovat na stejném dokumentu bez narušení formátování souboru.

Chcete-li otevřít možnosti projektu v Visual Studio pro Mac, poklikejte na název projektu, nebo kliknutím pravým tlačítkem otevřete místní nabídku a vyberte možnost **Možnosti**:

![Možnost v místní nabídce](media/projects-and-solutions-image2.png)

Možnosti úprav obsahují možnosti pro sestavování, spouštění a nastavování zdrojového kódu a správy verzí.

Možnosti projektu jsou uspořádány do pěti různých kategorií:

* **Obecné** – informace o projektu, jako je název, popis a výchozí obor názvů, jsou zde nastaveny společně s umístěním projektu.
* **Sestavení** – umožňuje vývojářům nastavovat nebo měnit profily PCL pro přenosné knihovny tříd. Umožňuje také nastavit vlastní příkazy, konfigurace, možnosti kompilátoru. Výstupní cestu a název sestavení lze také nastavit zde.
* **Spustit** – umožňuje vytvářet vlastní konfigurace spuštění na základě jednotlivých projektů.
* **Zdrojový kód** – umožňuje řídit formátování mnoha různých typů souborů a konvencí pojmenování. Tady můžete také nastavit zásady pojmenování a výchozí styly záhlaví.
* Správa **verzí** – umožňuje upravit styl zprávy potvrzení při použití správy verzí s vaším projektem.

Každý projekt může obsahovat konkrétní možnosti projektu v závislosti na platformě. Například projekt Xamarin. Android, podobně jako ten, který je znázorněný na následujícím obrázku, obsahuje možnosti týkající se sestavení pro Android (například možnosti linkeru) a aplikace (například oprávnění):

![Možnosti projektu pro Android](media/projects-and-solutions-image5.png)

Xamarin. iOS obsahuje možnosti týkající se podepisování sady, jako je třeba požadovaný zřizovací profil, který se má použít:

![Možnosti projektu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Možnosti řešení

Možnosti řešení jsou jako možnosti projektu, ale zahrnují rozsah celých řešení. Poskytují způsob, jak nastavit informace o autorech, nastavení sestavení, styly formátování kódu a správu verzí a umožňují způsob přiřazení spouštěného projektu v řešení.  K dialogovému oknu možnosti řešení lze přistupovat z položky nabídky **nastavení projektu > možnosti** , z kontextové nabídky **Možnosti** v řešení na panelu řešení nebo dvojím kliknutím na řešení v oblast řešení:

![Možnosti řešení](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Viz také:

* [Správa vlastností projektu a řešení (Visual Studio ve Windows)](/visualstudio/ide/managing-project-and-solution-properties)
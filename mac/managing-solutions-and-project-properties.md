---
title: Správa vlastností projektů a řešení
description: Tento článek popisuje, jak spravovat vlastnosti projektů a řešení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492994"
---
# <a name="managing-project-and-solution-properties"></a>Správa vlastností projektů a řešení

## <a name="project-options"></a>Možnosti projektů

Možnosti projektu jsou specifické pro každý projekt a mají vliv na to, jak je projekt napsán, sestaven a spuštěn. Na rozdíl od Visual Studio pro Mac předvoleb, které jsou uživatelsky specifická nastavení, jsou možnosti projektu uloženy v souboru projektu (. csproj), aby ostatní vývojáři mohli správně sestavit a spustit projekt. S konkrétními možnostmi projektu může mnoho vývojářů pracovat na stejném dokumentu bez narušení formátování souboru.

Chcete-li otevřít možnosti projektu v Visual Studio pro Mac, poklikejte na název projektu, nebo kliknutím pravým tlačítkem otevřete místní nabídku a vyberte možnost **Možnosti** :

![Možnost v místní nabídce](media/projects-and-solutions-image2.png)

Možnosti úprav obsahují možnosti pro sestavování, spouštění a nastavování zdrojového kódu a správy verzí.

Možnosti projektu jsou uspořádány do pěti různých kategorií:

* **Obecné** – informace o projektu, jako je název, popis a výchozí obor názvů, jsou zde nastaveny společně s umístěním projektu.
* **Sestavení** – slouží k nastavení nebo změně profilů PCL pro přenosné knihovny tříd. Umožňuje také nastavit vlastní příkazy, konfigurace, možnosti kompilátoru. Výstupní cestu a název sestavení lze také nastavit zde.
* **Spuštění** – slouží k vytvoření vlastních konfigurací spuštění na základě jednotlivých projektů.
* **Zdrojový kód** – řídí formátování mnoha různých typů souborů a konvencí pojmenování. Tady můžete také nastavit zásady pojmenování a výchozí styly záhlaví.
* Správa **verzí** – možnosti pro nastavení stylu potvrzení zprávy při použití správy verzí u vašeho projektu.

Každý projekt může obsahovat konkrétní možnosti projektu v závislosti na platformě. Například projekt Xamarin. Android, podobně jako ten, který je znázorněný na následujícím obrázku, obsahuje možnosti týkající se sestavení pro Android (například možnosti linkeru) a aplikace (například oprávnění):

![Možnosti projektu pro Android](media/projects-and-solutions-image5.png)

Xamarin. iOS obsahuje možnosti týkající se podepisování sady, jako je třeba požadovaný zřizovací profil, který se má použít:

![Možnosti projektu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Možnosti řešení

Možnosti řešení jsou jako možnosti projektu, ale zahrnují rozsah celých řešení. Poskytují způsob, jak nastavit informace o autorech, nastavení sestavení, styly formátování kódu a správu verzí a umožňují způsob přiřazení spouštěného projektu v řešení.  K dialogovému oknu možnosti řešení je možné přistupovat z položky nabídky **Možnosti projektu > možností** , z kontextové nabídky **Možnosti** v řešení v okně řešení nebo dvojím kliknutím na řešení v okně řešení:

![Možnosti řešení](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Viz také

* [Správa vlastností projektu a řešení (Visual Studio ve Windows)](/visualstudio/ide/managing-project-and-solution-properties)
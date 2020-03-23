---
title: Správa vlastností projektů a řešení
description: Tento článek popisuje, jak spravovat vlastnosti projektů a řešení v sadě Visual Studio for Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985264"
---
# <a name="managing-project-and-solution-properties"></a>Správa vlastností projektů a řešení

## <a name="project-options"></a>Možnosti projektů

Možnosti projektu jsou specifické pro každý projekt a ovlivňují způsob, jakým je projekt zapsán, sestaven a spuštěn. To kontrastuje s předvolbami Visual Studia for Mac (který nastavuje možnosti specifické pro uživatele) a možnostmi řešení (které nastavují možnosti pro celé řešení). Možnosti projektu jsou uloženy v souboru projektu (.csproj), takže ostatní vývojáři mohou sestavit a spustit projekt správně. S konkrétní možnosti projektu umožňuje mnoho vývojářů pracovat na stejném dokumentu bez ohrožení formátování souboru.

Pokud chcete v Visual Studiu for Mac otevřít možnosti Projectu, poklikejte na název projektu nebo kliknutím pravým tlačítkem otevřete místní nabídku a pak vyberte **Možnosti**:

![Možnost v kontextové nabídce](media/projects-and-solutions-image2.png)

Možnosti úprav zahrnují možnosti sestavení, spuštění a nastavení správy zdrojového kódu a verze.

Možnosti projektu jsou uspořádány do pěti různých kategorií:

* **Obecné** – zde jsou nastaveny informace o projektu, jako je název, popis a výchozí obor názvů, spolu s umístěním projektu.
* **Sestavení** – to umožňuje vývojářům nastavit nebo změnit profily PCL pro knihovny přenosných tříd. Umožňuje také nastavit vlastní příkazy, konfigurace, možnosti kompilátoru. Zde lze také nastavit výstupní cestu a název sestavení.
* **Spustit** – to umožňuje vytvořit vlastní spuštění konfigurace na základě projektu.
* **Zdrojový kód** – to umožňuje řídit formátování mnoha různých typů souborů a konvencí pojmenování. Zde můžete také nastavit zásady pojmenování a výchozí styly záhlaví.
* **Správa verzí** – to umožňuje upravit styl zprávy potvrzení při použití správy verzí s projektem.

Každý projekt může obsahovat konkrétní možnosti projektu, v závislosti na platformě. Například projekt Xamarin.Android, jako je znázorněno na následujícím obrázku, má možnosti týkající se sestavení Androidu (například možnosti propojovacího zařízení) a aplikace (například oprávnění):

![Možnosti projektu Android](media/projects-and-solutions-image5.png)

Xamarin.iOS má možnosti související s podepisováním balíčků – například požadovaný profil zřizování, který chcete použít:

![Možnosti projektu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Možnosti řešení

Možnosti řešení jsou jako možnosti projektu, ale pokrývají rozsah celé řešení. Poskytují způsob, jak nastavit informace o autorovi, nastavení sestavení, styly formátování kódu a správu verzí a umožňují způsob přiřazení projektu spuštění v řešení.  Dialogové okno Možnosti řešení lze získat z položky nabídky **Možnosti řešení projektu >,** z položky kontextové nabídky **Možnosti** v panelu Řešení nebo poklepáním na řešení na panelu řešení:

![Možnosti řešení](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Viz také

* [Správa vlastností projektu a řešení (Visual Studio v systému Windows)](/visualstudio/ide/managing-project-and-solution-properties)
---
title: Hledání a nahrazování v souborech
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585623"
---
# <a name="replace-in-files"></a>Nahradit v souborech

**Nahradit v souborech** umožňuje prohledávat kód zadané sady souborů pro řetězec nebo výraz a změnit některé nebo všechny nalezené shody. Nalezené shody a provedené akce jsou uvedeny v okně **Najít výsledky** vybrané v **části Možnosti výsledku**.

> [!NOTE]
> Zobrazená dialogová okna a příkazy nabídek se mohou lišit od těch, které jsou popsány v **nápovědě,** v závislosti na aktivním nastavení nebo edici. Chcete-li změnit nastavení, například **na Obecné** nebo Vizuální **nastavení c++,** zvolte **Nástroje** > **Import a export nastavení**a pak zvolte Obnovit všechna **nastavení**.

K zobrazení **nahradit v souborech v** okně **Najít a nahradit** můžete použít některou z následujících metod.

## <a name="to-display-replace-in-files"></a>Zobrazení nahradit v souborech

1. V nabídce **Úpravy** rozbalte **možnost Najít a nahradit**.

2. Zvolte **Nahradit v souborech**.

   — nebo —

   Pokud je již otevřené okno **Najít a nahradit,** na panelu nástrojů zvolte **Nahradit v souborech**.

## <a name="find-what"></a>Najít

Chcete-li vyhledat nový textový řetězec nebo výraz, zadejte jej do pole. Chcete-li vyhledat některý z 20 řetězců, které jste naposledy hledali, otevřete rozevírací seznam a zvolte řetězec. Pokud chcete ve vyhledávacím řetězci použít jeden nebo více regulárních výrazů, zvolte sousední tlačítko **Tvůrce výrazů.** Další informace naleznete v [tématu Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Tlačítko **Tvůrce výrazů** bude povoleno pouze v případě, že jste v části **Možnosti hledání**vybrali **možnosti Použít regulární výrazy** .

## <a name="replace-with"></a>Nahradit hodnotou

Chcete-li nahradit instance řetězce v poli **Najít** jiným řetězcem, zadejte náhradní řetězec do pole **Nahradit.** Chcete-li odstranit instance řetězce v poli **Najít,** ponechte toto pole prázdné. Otevřete seznam a zobrazte 20 řetězců, které jste naposledy hledali. Pokud chcete v náhradním řetězci použít jeden nebo více regulárních výrazů, zvolte sousední tlačítko **Tvůrce výrazů.** Další informace naleznete v [tématu Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Podívejte se dovnitř

Možnost zvolená v rozevíracím seznamu **Hledat v** určuje, zda funkce Nahradit **v souborech** vyhledá v aktuálně aktivních souborech nebo prohledá všechny soubory uložené v určitých složkách. Vyberte obor hledání ze seznamu, zadejte cestu ke složce nebo klepněte na tlačítko **Procházet (...)** a zobrazte dialogové okno **Zvolit složky výsledků hledání** a zvolte sadu složek, které chcete prohledat. Cestu můžete také zadat přímo do pole **Hledat v.**

> [!NOTE]
> Pokud vybraná možnost **Hledat** způsobí, že prohledáte soubor, který jste si vybrali ze správy zdrojového kódu, bude prohledána pouze verze tohoto souboru, která byla stažena do místního počítače.

## <a name="find-options"></a>Najít možnosti

Oddíl **Najít možnosti** můžete rozbalit nebo sbalit. Lze vybrat nebo vymazat následující možnosti:

**Rozlišovat velikost písmen**

Když je tato volba vybraná, v oknech **Najít výsledky** se zobrazí pouze instance řetězce **Najít,** který je shodou obsahu i podle případu. Například hledání "MyObject" s **Match případ** vybrané vrátí "MyObject", ale ne "myobject" nebo "MYOBJECT."

**Shoda celého slova**

Když je tato volba vybraná, v oknech **Najít výsledky** se zobrazí pouze instance řetězce **Najít,** který je spárován s úplnými slovy. Například hledání "MyObject" vrátí "MyObject", ale ne "CMyObject" nebo "MyObjectC."

**Použití regulárních výrazů**

Pokud je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu v polích **Najít co** nebo **Nahradit** textem. Seznam těchto zápisů naleznete v tématu [Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů**

Tento seznam označuje typy souborů, které mají být prohledány v adresářích **Hledat** v adresářích. Pokud je toto pole prázdné, budou prohledány všechny soubory v části **Hledat v** adresářích. Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný vyhledávací řetězec, který najde soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledků

Oddíl **Možnosti výsledek** můžete rozbalit nebo sbalit. Lze vybrat nebo vymazat následující možnosti:

**Okno Najít výsledky 1**

Pokud je tato možnost vybrána, výsledky aktuálního hledání nahradí obsah okna **Najít výsledky 1.** Toto okno se otevře automaticky, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, vyberte v nabídce **Zobrazení** **položku Jiný systém Windows** a zvolte Najít **výsledky 1**.

**Okno Najít výsledky 2**

Pokud je tato možnost vybrána, výsledky aktuálního hledání nahradí obsah okna **Najít výsledky 2.** Toto okno se otevře automaticky, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, vyberte v nabídce **Zobrazení** položku **Jiný systém Windows** a zvolte Najít výsledky **2**.

**Pouze zobrazované názvy souborů**

Je-li toto políčko zaškrtnuto, zobrazí se v oknech **Najít výsledky** úplné názvy a cesty pro všechny soubory, které obsahují hledaný řetězec. Výsledky však neobsahují řádek kódu, kde se řetězec zobrazí. Toto zaškrtávací políčko je k dispozici pouze pro **hledání v souborech.**

**Zachovat upravené soubory otevřené po nahradit vše**

Je-li tato možnost vybrána, ponechá všechny soubory, ve kterých byly provedeny náhrady, takže změny můžete vrátit zpět nebo uložit. Omezení paměti může omezit počet souborů, které mohou zůstat otevřené po operaci nahrazení.

> [!CAUTION]
> **Příkaz Vrátit příkaz lze** použít pouze u souborů, které zůstávají otevřené pro úpravy. Pokud tato možnost není vybrána, soubory, které ještě nebyly otevřeny pro úpravy, zůstanou v těchto souborech uzavřeny a nebude v nich k dispozici žádná možnost **Vrátit.**

## <a name="see-also"></a>Viz také

- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
- [Hledání v souborech](../ide/find-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)

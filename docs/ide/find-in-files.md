---
title: Najít v souborech
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595472"
---
# <a name="find-in-files"></a>Najít v souborech

**Najít v souborech** umožňuje prohledávat zadanou sadu souborů. Nalezené shody a provedené akce jsou uvedeny v okně **Najít výsledky** vybrané v **části Možnosti výsledku**.

K zobrazení **hledání v souborech v** okně **Najít a nahradit** můžete použít některou z následujících metod.

## <a name="to-display-find-in-files"></a>Zobrazení funkce Najít v souborech

1. Na řádku nabídek zvolte **Upravit** > **hledání a nahradit**.

1. Zvolte **Najít v souborech**.

Operaci Hledání zrušíte stisknutím **klávesctrl** + **.**

> [!NOTE]
> Nástroj najít a nahradit neprohledává `Hidden` `System` adresáře s atributem nebo.

## <a name="find-what"></a>Najít

Chcete-li vyhledat nový textový řetězec nebo výraz, zadejte jej do pole. Chcete-li vyhledat některý z 20 řetězců, které jste naposledy hledali, otevřete rozevírací seznam a zvolte řetězec. Pokud chcete ve vyhledávacím řetězci použít jeden nebo více regulárních výrazů, zvolte sousední tlačítko **Tvůrce výrazů.** Další informace naleznete [v tématu Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Tlačítko **Tvůrce výrazů** bude povoleno pouze v případě, že jste v části **Možnosti hledání**vybrali **možnosti Použít regulární výrazy** .

## <a name="look-in"></a>Podívejte se dovnitř

Možnost zvolená v rozevíracím seznamu **Hledat v** určuje, zda hledání **v souborech** vyhledá v souborech pouze v aktuálně aktivních souborech nebo ve všech souborech uložených v určitých složkách. Vyberte obor hledání ze seznamu nebo klepnutím na tlačítko **Procházet (...)** zobrazte dialogové okno **Zvolit složky výsledků hledání** a zadejte vlastní sadu adresářů. Cestu můžete také zadat přímo do pole **Hledat v.**

> [!WARNING]
> S **možnostmi Celé řešení** nebo **Aktuální projekt** nejsou prohledávány soubory projektu a řešení. Pokud chcete hledat v souborech projektu, zvolte složku hledání.

> [!NOTE]
> Pokud vybraná možnost **Hledat** způsobí, že prohledáte soubor, který jste si vybrali ze správy zdrojového kódu, bude prohledána pouze verze tohoto souboru, která byla stažena do místního počítače.

## <a name="include-subfolders"></a>Zahrnout podsložky

Určuje, že budou prohledány podsložky složky **Hledat ve.**

## <a name="find-options"></a>Najít možnosti

Oddíl **Najít možnosti** můžete rozbalit nebo sbalit. Lze vybrat nebo vymazat následující možnosti:

**Rozlišovat velikost písmen**

Je-li tato možnost vybrána, bude hledání **výsledků hledání** rozlišováno

**Shoda celého slova**

Je-li tato možnost vybrána, vrátí se v oknech **Hledání výsledků** pouze celá shoda slov.

**Použití regulárních výrazů**

Pokud je toto políčko zaškrtnuto, můžete pomocí speciálních zápisů definovat vzorky textu tak, aby odpovídaly v polích **Najít co** nebo **Nahradit** textem. Seznam těchto zápisů naleznete v tématu [Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů**

Tento seznam označuje typy souborů, které mají být prohledány v adresářích **Hledat** v adresářích. Pokud je toto pole prázdné, budou prohledány všechny soubory v části **Hledat v** adresářích.

Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný vyhledávací řetězec, který najde soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledků

Oddíl **Možnosti výsledek** můžete rozbalit nebo sbalit. Lze vybrat nebo vymazat následující možnosti:

**Najít výsledky 1 okno**

Pokud je tato možnost vybrána, výsledky aktuálního hledání nahradí obsah okna **Najít výsledky 1.** Toto okno se otevře automaticky, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, vyberte v nabídce **Zobrazení** **položku Jiný systém Windows** a zvolte Najít **výsledky 1**.

**Najít výsledky 2 okno**

Pokud je tato možnost vybrána, výsledky aktuálního hledání nahradí obsah okna **Najít výsledky 2.** Toto okno se otevře automaticky, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, vyberte v nabídce **Zobrazení** položku **Jiný systém Windows** a zvolte Najít výsledky **2**.

**Pouze zobrazované názvy souborů**

Zobrazí seznam souborů obsahujících shody hledání, nikoli zobrazení shod hledání samotných.

**Připojit výsledky**

Připojí výsledky z hledání k předchozím výsledkům hledání.

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../ide/replace-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)

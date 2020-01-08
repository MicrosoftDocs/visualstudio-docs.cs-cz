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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595472"
---
# <a name="find-in-files"></a>Najít v souborech

**V části soubory** můžete vyhledat zadanou sadu souborů. Nalezených shod a akcí provedených jsou uvedeny v **výsledky hledání** vybraný v interval **způsobit možnosti**.

Pomocí kterékoli z následujících metod můžete v okně **Najít a nahradit** zobrazit **najít v souborech** .

## <a name="to-display-find-in-files"></a>Zobrazení souborů hledání v souborech

1. Na panelu nabídek vyberte možnost **upravit** > **Najít a nahradit**.

1. Vyberte **najít v souborech**.

Operaci hledání zrušíte stisknutím klávesy **Ctrl** + **Break**.

> [!NOTE]
> Nástroj najít a nahradit nehledá adresáře s atributem `Hidden` nebo `System`.

## <a name="find-what"></a>Najít

K vyhledání nový textový řetězec nebo výraz, zadejte do pole. Chcete-li vyhledávat libovolné 20 řetězců, které jste hledali naposledy, otevřete rozevírací seznam a zvolte řetězec. Zvolte sousedních **Tvůrce výrazů** tlačítko, pokud chcete použít jeden nebo více regulární výrazy ve vyhledávaném řetězci. Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Tvůrce výrazů** tlačítko bude povoleno pouze pokud jste vybrali **pomocí regulárních výrazů** pod **možnosti hledání**.

## <a name="look-in"></a>Oblast hledání

Možnost zvolená v rozevíracím seznamu **Hledat v** souboru určuje, zda funkce **najít v souborech** vyhledává pouze v aktuálně aktivních souborech nebo ve všech souborech uložených v určitých složkách. Vyberte obor vyhledávání ze seznamu nebo klikněte na tlačítko **Procházet (...)** a zobrazte dialogové okno **Zvolit složky výsledků hledání** a zadejte vlastní sadu adresářů. Můžete také zadat přímo do cesty **Hledat v** pole.

> [!WARNING]
> V rámci **celého řešení** nebo **aktuálních možností projektu** nejsou prohledávány soubory projektu a řešení. Pokud chcete hledat v souborech projektu, vyberte složku výsledků hledání.

> [!NOTE]
> Pokud **Hledat v** zaškrtnutou možnost způsobí, že vám umožní vyhledávat soubor, který jste rezervovali ve správě zdrojového kódu, je prohledána pouze verze tohoto souboru, který byl stažen do místního počítače.

## <a name="include-subfolders"></a>Zahrnout podsložky

Určuje, že se budou Prohledávat podsložky složky **Hledat ve** složce.

## <a name="find-options"></a>Možnosti hledání

Můžete rozbalit nebo sbalit **možnosti hledání** oddílu. Následující možnosti můžete vybrané nebo zrušeno:

**Rozlišovat velikost písmen**

Pokud je tato možnost vybrána, bude hledání **výsledků** hledání rozlišovat velká a malá písmena.

**Pouze celá slova**

Pokud je tato možnost vybrána, okna **výsledků hledání** budou vracet pouze celá slova.

**Používání regulárních výrazů**

Pokud je toto políčko zaškrtnuté, můžete použít speciální zápisy k definování vzorů textu, které se budou shodovat s textovými poli **Najít** nebo **nahradit** . Seznam těchto zápisů naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů**

Tento seznam uvádí typy souborů pro hledání prostřednictvím v **Hledat v** adresáře. Pokud je toto pole prázdné, prohledávají se všechny soubory v adresářích **Hledat v** .

Vyberte libovolnou položku v seznamu a zadejte předkonfigurované vyhledávací řetězec, který najdete tyto konkrétní typy souborů.

## <a name="result-options"></a>Možnosti výsledků

Můžete rozbalit nebo sbalit **způsobit možnosti** oddílu. Následující možnosti můžete vybrané nebo zrušeno:

**Okno výsledky hledání 1**

Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 1** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 1**.

**Okno výsledky hledání 2**

Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 2** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 2**.

**Zobrazit pouze názvy souborů**

Zobrazí seznam souborů, které obsahují shody hledání, místo zobrazení shod se stejnými výsledky hledání.

**Připojit výsledky**

Připojí výsledky hledání k předchozím výsledkům hledání.

## <a name="see-also"></a>Viz také:

- [Hledání a nahrazování textu](../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../ide/replace-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)

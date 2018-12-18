---
title: Najít v souborech
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1470868e207687a7b35f46724b80b0da0a0e71c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946556"
---
# <a name="find-in-files"></a>Najít v souborech

**Hledání v souborech** umožňuje hledat zadané sady souborů. Nebyla nalezena shoda a akcí provedených jsou uvedeny v **Najít výsledky** vybrán v okně **způsobit možnosti**.

K zobrazení můžete použít některou z následujících metod **hledání v souborech** v **najít a nahradit** okno.

## <a name="to-display-find-in-files"></a>Chcete-li zobrazit najít v souborech

1. Na řádku nabídek zvolte **upravit** > **najít a nahradit**.

1. Zvolte **hledání v souborech**.

Chcete-li zrušit operaci hledání, stiskněte **Ctrl** + **rozdělit**.

> [!NOTE]
> Nástroj Najít a nahradit neprohledává adresářů pomocí `Hidden` nebo `System` atribut.

## <a name="find-what"></a>Najít

Vyhledat nový textový řetězec nebo výraz, zadejte do pole. Chcete-li vyhledávat libovolné 20 řetězce, které jste hledali naposledy, otevřete rozevírací seznam a zvolte řetězec. Zvolte sousedním **Tvůrce** tlačítko, pokud chcete použít jeden nebo více regulární výrazy v hledanému řetězci. Další informace najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Tvůrce** tlačítko bude povoleno pouze pokud jste vybrali **pomocí regulárních výrazů** pod **najít možnosti**.

## <a name="look-in"></a>Oblast hledání

Možnost výběru z **naleznete v** rozevíracího seznamu určuje, zda **hledání v souborech** hledání pouze v aktuálně aktivních souborů nebo všechny soubory uložené v rámci určitých složek. Obor vyhledávání vyberte ze seznamu nebo klikněte na **Procházet (...)**  tlačítko pro zobrazení **zvolte složky výsledků hledání** dialogové okno a zadejte vlastní sadu adresáře. Můžete také zadat cestu přímo do **Hledat v** pole.

> [!WARNING]
> S **celé řešení** nebo **aktuálního projektu** se neprohledávají soubory možnosti, projektů a řešení. Pokud chcete hledat v souborech projektu, zvolte složku výsledků hledání.

> [!NOTE]
> Pokud **Hledat v** možnost způsobí, že jste k vyhledání souboru, který máte rezervován od správy zdrojového kódu, prohledají se jenom verze tohoto souboru, který byl stažen do místního počítače.

## <a name="include-subfolders"></a>Zahrnout podsložky

Určuje, že podsložky **naleznete v** prohledá složku.

## <a name="find-options"></a>Možnosti hledání

Můžete rozbalit nebo sbalit **najít možnosti** části. Následující možnosti může být vybrána nebo vymazána:

**Malá a velká písmena**

Při výběru **Najít výsledky** hledání bude malá a velká písmena

**Celá slova**

Při výběru, **Najít výsledky** windows vrátí jenom celá slova odpovídá.

**Používání regulárních výrazů**

Pokud je toto políčko zaškrtnuto, můžete použít speciální zápisy zadat textovou tak, aby odpovídaly v **najít** nebo **nahraďte** textových polí. Seznam těchto zápisy, naleznete v části [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů**

Tento seznam uvádí typy souborů, pokud chcete hledat v **Hledat v** adresáře. Pokud je tato pole prázdná, všechny soubory v **Hledat v** prohledávaných adresářů.

Vyberte libovolnou položku v seznamu a zadejte předkonfigurované vyhledávací řetězec, který zjistí tyto konkrétní typy souborů.

## <a name="result-options"></a>Možnosti výsledku

Můžete rozbalit nebo sbalit **způsobit možnosti** části. Následující možnosti může být vybrána nebo vymazána:

**Najít okno výsledků 1**

Pokud vybraná, výsledky hledání aktuální nahradí obsah **najít 1 výsledky** okno. Toto okno se automaticky otevře a zobrazí výsledky hledání. Otevřete toto okno ručně, vyberte **ostatní okna** z **zobrazení** nabídky a zvolte **najít 1 výsledky**.

**Najít okno výsledků 2**

Pokud vybraná, výsledky hledání aktuální nahradí obsah **najít 2 výsledky** okno. Toto okno se automaticky otevře a zobrazí výsledky hledání. Otevřete toto okno ručně, vyberte **ostatní okna** z **zobrazení** nabídky a zvolte **najít 2 výsledky**.

**Zobrazit pouze názvy souborů**

Zobrazí seznam souborů obsahující hledání odpovídá místo zobrazení hledání odpovídá sami.

**Append – výsledky**

Připojí výsledků vyhledávání do předchozí výsledky hledání.

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../ide/replace-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)
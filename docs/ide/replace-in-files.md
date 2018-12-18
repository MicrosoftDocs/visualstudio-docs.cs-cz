---
title: Najít a nahradit v souborech
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 625cb98391199bad78fb4492e635b2b1767debe7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057876"
---
# <a name="replace-in-files"></a>Nahradit v souborech

**Nahradit v souborech** umožňuje vyhledávání kódu zadané sady souborů pro řetězec nebo výraz a změnit některé nebo všechny nalezených shod. Nalezených shod a akcí provedených jsou uvedeny v **výsledky hledání** vybraný v interval **způsobit možnosti**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, zobrazí se mohou lišit od těch popsaných v **pomáhají** v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, například k **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje** > **nastavení importu a exportu**a klikněte na tlačítko **obnovit všechna nastavení**.

Můžete použít některý z následujících metod k zobrazení **nahradit v souborech** v **najít a nahradit** okna.

## <a name="to-display-replace-in-files"></a>Chcete-li zobrazit nahradit v souborech

1. Na **upravit** nabídky, rozbalte **najít a nahradit**.

2. Zvolte **nahradit v souborech**.

   – nebo –

   Pokud **najít a nahradit** , je již otevřeno, na panelu nástrojů zvolte **nahradit v souborech**.

## <a name="find-what"></a>Najít

K vyhledání nový textový řetězec nebo výraz, zadejte do pole. Chcete-li vyhledávat libovolné 20 řetězců, které jste hledali naposledy, otevřete rozevírací seznam a zvolte řetězec. Zvolte sousedních **Tvůrce výrazů** tlačítko, pokud chcete použít jeden nebo více regulární výrazy ve vyhledávaném řetězci. Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Tvůrce výrazů** tlačítko bude povoleno pouze pokud jste vybrali **pomocí regulárních výrazů** pod **možnosti hledání**.

## <a name="replace-with"></a>Nahraďte

K nahrazení výskytů řetězce v **najít** jiným řetězcem, zadejte v řetězci pro nahrazení **nahradit** pole. Chcete-li odstranit výskytů řetězce v **najít** pole, toto pole nechat prázdné. Otevřete seznam pro zobrazení 20 řetězců, u kterých je prohledán jako poslední. Zvolte sousedních **Tvůrce výrazů** tlačítko, pokud chcete použít jeden nebo více regulárních výrazů v řetězci pro nahrazení. Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Oblast hledání

Možnost výběru z **Hledat v** rozevíracího seznamu určuje, zda **nahradit v souborech** vyhledá pouze v současné době aktivní soubory, nebo vyhledá všechny soubory uložené v určitých složkách. Vyberte obor hledání v seznamu, zadejte cestu ke složce nebo klikněte na tlačítko **Procházet (...)**  tlačítka pro zobrazení **zvolit složky pro hledání** dialogového okna a vyberte sadu složek k prohledání. Můžete také zadat přímo do cesty **Hledat v** pole.

> [!NOTE]
> Pokud **Hledat v** zaškrtnutou možnost způsobí, že vám umožní vyhledávat soubor, který jste rezervovali ve správě zdrojového kódu, je prohledána pouze verze tohoto souboru, který byl stažen do místního počítače.

## <a name="find-options"></a>Možnosti hledání

Můžete rozbalit nebo sbalit **možnosti hledání** oddílu. Následující možnosti můžete vybrané nebo zrušeno:

**Rozlišovat velikost písmen**

Při výběru **výsledky hledání** windows budou zobrazovat jenom instance **najít** řetězec, který budou odpovídat podle obsahu a případem. Například vyhledejte "MyObject" s **rozlišovat velikost písmen** vybrané se vrátí "MyObject" ale ne "myobject" nebo "MYOBJECT."

**Pouze celá slova**

Pokud je vybráno, **výsledky hledání** windows budou zobrazovat jenom instance **najít** řetězec, který se shodují v celá slova. Například vyhledejte "MyObject" vrátí "MyObject", ale není "CMyObject" nebo "MyObjectC."

**Používání regulárních výrazů**

Když je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu v **najít** nebo **nahraďte** textová pole. Seznam těchto zápisy najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů**

Tento seznam uvádí typy souborů pro hledání prostřednictvím v **Hledat v** adresáře. Pokud je toto pole necháte prázdné, všechny soubory v **Hledat v** budou prohledány adresáře. Vyberte libovolnou položku v seznamu a zadejte předkonfigurované vyhledávací řetězec, který najdete tyto konkrétní typy souborů.

## <a name="result-options"></a>Možnosti výsledků

Můžete rozbalit nebo sbalit **způsobit možnosti** oddílu. Následující možnosti můžete vybrané nebo zrušeno:

**Najít výsledky 1** okna

Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 1** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 1**.

**Najít výsledky 2** okna

Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 2** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 2**.

**Zobrazit pouze názvy souborů**

Když je toto políčko zaškrtnuto, **výsledky hledání** windows seznamu úplné názvy dnů a cesty pro všechny soubory, které obsahují hledaný řetězec. Výsledky jsou však na řádek kódu, kde se zobrazí řetězec. Toto zaškrtávací políčko je dostupné pro **najít v souborech** pouze.

**Ponechat změněné soubory otevřené po Nahradit vše**

Při výběru, otevřete všechny soubory zůstanou ve kterých nahrazení byly provedeny, můžete vrátit zpět nebo uložte změny. Omezení paměti může být omezen počet souborů, které může zůstat otevřené po operaci nahradit.

> [!CAUTION]
> Můžete použít **zpět** pouze u souborů, které zůstanou otevřené pro úpravy. Pokud tato možnost není vybraná, soubory, které ještě nebyly otevřete pro úpravy zůstanou uzavřené a ne **zpět** možnost je k dispozici v těchto souborech.

## <a name="see-also"></a>Viz také:

- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
- [Najít v souborech](../ide/find-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)

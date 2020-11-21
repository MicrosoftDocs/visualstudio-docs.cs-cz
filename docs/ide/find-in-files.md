---
title: Najít v souborech
description: Přečtěte si o funkci najít v souborech a o tom, jak ji použít k prohledávání konkrétní sady souborů.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c9aa0d1523c8ef8be73a3c5e73255ce1eeb32d57
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006572"
---
# <a name="find-in-files"></a>Najít v souborech

**V části soubory** můžete vyhledat zadanou sadu souborů. Nalezené shody a podniknuté akce jsou uvedeny v okně **výsledky hledání** vybrané v **Možnosti výsledek**.

Pomocí kterékoli z následujících metod můžete v okně **Najít a nahradit** zobrazit **najít v souborech** .

## <a name="to-display-find-in-files"></a>Zobrazení souborů hledání v souborech

1. Na řádku nabídek klikněte na příkaz **Upravit**  >  **Najít a nahradit**.

1. Vyberte **najít v souborech**.

Operaci hledání zrušíte stisknutím klávesy **CTRL**  +  **Break**.

> [!NOTE]
> Nástroj najít a nahradit nehledá adresáře s `Hidden` `System` atributem nebo.

## <a name="find-what"></a>Najít

Pokud chcete vyhledat nový textový řetězec nebo výraz, zadejte ho do pole. Pokud chcete vyhledat kterýkoli z 20 řetězců, které jste prohledali naposledy, otevřete rozevírací seznam a vyberte řetězec. Pokud chcete v hledaném řetězci použít jeden nebo více regulárních výrazů, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Tlačítko **Tvůrce výrazů** bude povoleno pouze v případě, že jste vybrali možnost **použít regulární výrazy** v části **Možnosti hledání**.

## <a name="look-in"></a>Oblast hledání

Možnost zvolená v rozevíracím seznamu **Hledat v** souboru určuje, zda funkce **najít v souborech** vyhledává pouze v aktuálně aktivních souborech nebo ve všech souborech uložených v určitých složkách. Vyberte obor vyhledávání ze seznamu nebo klikněte na tlačítko **Procházet (...)** a zobrazte dialogové okno **Zvolit složky výsledků hledání** a zadejte vlastní sadu adresářů. Můžete také zadat cestu přímo do pole **Hledat v** .

> [!WARNING]
> V rámci **celého řešení** nebo **aktuálních možností projektu** nejsou prohledávány soubory projektu a řešení. Pokud chcete hledat v souborech projektu, vyberte složku výsledků hledání.

> [!NOTE]
> Pokud vybraná možnost **Hledat v** způsobí hledání souboru, který jste si rezervovali ze správy zdrojového kódu, prohledává se jenom verze tohoto souboru, který se stáhl do místního počítače.

## <a name="include-subfolders"></a>Zahrnout podsložky

Určuje, že se budou Prohledávat podsložky složky **Hledat ve** složce.

## <a name="find-options"></a>Možnosti hledání

Můžete rozbalit nebo sbalit část **Možnosti hledání** . Můžete vybrat nebo vymazat následující možnosti:

**Rozlišovat velikost písmen**

Pokud je tato možnost vybrána, bude hledání **výsledků** hledání rozlišovat velká a malá písmena.

**Vyhledat celé slovo**

Pokud je tato možnost vybrána, okna **výsledků hledání** budou vracet pouze celá slova.

**Použití regulárních výrazů**

Pokud je toto políčko zaškrtnuté, můžete použít speciální zápisy k definování vzorů textu, které se budou shodovat s textovými poli **Najít** nebo **nahradit** . Seznam těchto zápisů naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů.**

Tento seznam uvádí typy souborů, které se mají hledat v adresářích **Hledat v** . Pokud je toto pole prázdné, prohledávají se všechny soubory v adresářích **Hledat v** .

Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný hledaný řetězec, ve kterém budou nalezeny soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledku

Oddíl **možností výsledků** můžete rozbalit nebo sbalit. Můžete vybrat nebo vymazat následující možnosti:

**Okno výsledky hledání 1**

Pokud je tato možnost vybrána, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 1** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 1**.

**Okno výsledky hledání 2**

Pokud je tato možnost vybrána, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 2** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 2**.

**Zobrazit pouze názvy souborů**

Zobrazí seznam souborů, které obsahují shody hledání, místo zobrazení shod se stejnými výsledky hledání.

**Připojit výsledky**

Připojí výsledky hledání k předchozím výsledkům hledání.

## <a name="see-also"></a>Viz také

- [Hledání a nahrazování textu](../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../ide/replace-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)
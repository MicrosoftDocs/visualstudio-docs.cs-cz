---
title: Najít v souborech | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655904"
---
# <a name="find-in-files"></a>Najít v souborech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hledání v souborech * * umožňuje vyhledat zadanou sadu souborů. Nalezené shody a podniknuté akce jsou uvedeny v okně **výsledky hledání** vybrané v **Možnosti výsledek**.

 Pomocí kterékoli z následujících metod můžete v okně **Najít a nahradit** zobrazit **najít v souborech** .

### <a name="to-display-find-in-files"></a>Zobrazení souborů hledání v souborech

1. Na řádku nabídek klikněte na položku **Upravit**, **Najít a nahradit**.

2. Vyberte **najít v souborech**.

   Operaci hledání zrušíte stisknutím kombinace kláves CTRL + BREAK.

> [!NOTE]
> Nástroj najít a nahradit nehledá adresáře s `Hidden` `System` nastaveným atributem nebo.

## <a name="find-what"></a>Najít
 Pokud chcete vyhledat nový textový řetězec nebo výraz, zadejte ho do pole. Chcete-li vyhledat kterýkoli z 20 řetězců, které jste prohledali naposledy, otevřete seznam a vyberte řetězec, který chcete vyhledat. Pokud chcete v hledaném řetězci použít jeden nebo více regulárních výrazů, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

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

 Při výběru rozlišovat velká a malá písmena, hledání **výsledků** hledání se rozlišuje velká a malá písmena.

 Porovná celé slovo, pokud je vybráno, okna **výsledků hledání** budou vracet pouze celá slova.

 Použijte regulární výrazy, pokud je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu tak, aby odpovídaly v textových polích **Najít** nebo **nahradit** . Seznam těchto zápisů naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Podívejte se na tyto typy souborů: Tento seznam uvádí typy souborů, které se mají hledat v adresářích **Hledat v** adresáři. Pokud je toto pole prázdné, prohledávají se všechny soubory v adresářích **Hledat v** .

 Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný hledaný řetězec, ve kterém budou nalezeny soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledku
 Oddíl **možností výsledků** můžete rozbalit nebo sbalit. Můžete vybrat nebo vymazat následující možnosti:

 Pokud je vybráno okno výsledky hledání 1, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 1** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 1**.

 Pokud je vybráno okno výsledky hledání 2, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 2** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 2**.

 Zobrazované názvy souborů zobrazí jenom seznam souborů, které obsahují shody hledání, a nikoli zobrazení shod samotného hledání.

 K připojením výsledků se zobrazí výsledky z hledání do předchozích výsledků hledání.

## <a name="see-also"></a>Viz také
 [Hledání a nahrazování nahrazování textu](../ide/finding-and-replacing-text.md) [v souborech](../ide/replace-in-files.md) [Visual Studio Commands](../ide/reference/visual-studio-commands.md)

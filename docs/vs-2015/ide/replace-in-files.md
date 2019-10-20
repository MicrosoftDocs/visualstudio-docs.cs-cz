---
title: Nahradit v souborech | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669964"
---
# <a name="replace-in-files"></a>Nahradit v souborech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nahradit v souborech * * umožňuje vyhledat v kódu zadanou sadu souborů pro řetězec nebo výraz a změnit některé nebo všechny nalezené shody. Nalezené shody a podniknuté akce jsou uvedeny v okně **výsledky hledání** vybrané v **Možnosti výsledek**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Pomocí kterékoli z následujících metod můžete v okně **Najít a nahradit** zobrazit **nahradit v souborech** .

### <a name="to-display-replace-in-files"></a>Zobrazení nahrazení v souborech

1. V nabídce **Upravit** rozbalte **Najít a nahradit**.

2. **V souborech vyberte nahradit**.

     ani

     Pokud je okno **Najít a nahradit** již otevřeno, na panelu nástrojů vyberte **nahradit v souborech**.

## <a name="find-what"></a>Najít
 Pokud chcete vyhledat nový textový řetězec nebo výraz, zadejte ho do pole. Chcete-li vyhledat kterýkoli z 20 řetězců, které jste prohledali naposledy, otevřete seznam a vyberte řetězec, který chcete vyhledat. Pokud chcete v hledaném řetězci použít jeden nebo více regulárních výrazů, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Nahradit
 Chcete-li nahradit výskyty řetězce v poli **Najít** s jiným řetězcem, zadejte v poli **Nahradit za** řetězec pro nahrazení. Pokud chcete odstranit instance řetězce v poli **Najít** , ponechte toto pole prázdné. Otevřete seznam pro zobrazení 20 řetězců, pro které jste prohledali poslední. Pokud chcete použít jeden nebo více regulárních výrazů v řetězci pro nahrazení, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Oblast hledání
 Možnost zvolená v rozevíracím seznamu **Hledat v** souboru určuje, zda funkce **nahradit v souborech** vyhledává pouze aktuálně aktivní soubory, nebo prohledává všechny soubory uložené v určitých složkách. V seznamu vyberte obor vyhledávání, zadejte cestu ke složce nebo klikněte na tlačítko **Procházet (...)** a zobrazte dialogové okno **Zvolit složky výsledků hledání** a zvolte sadu složek, které chcete vyhledat. Můžete také zadat cestu přímo do pole **Hledat v** .

> [!NOTE]
> Pokud vybraná možnost **Hledat v** způsobí hledání souboru, který jste si rezervovali ze správy zdrojového kódu, prohledává se jenom verze tohoto souboru, který se stáhl do místního počítače.

## <a name="find-options"></a>Možnosti hledání
 Můžete rozbalit nebo sbalit část **Možnosti hledání** . Můžete vybrat nebo vymazat následující možnosti:

 Při výběru rozlišovat velká a malá písmena. v oknech **výsledků hledání** se zobrazí pouze instance **hledaného** řetězce, které odpovídají obsahu i podle velikosti písmen. Například hledání typu "" v "s vybraným **případem shody** vrátí" "", ale ne "", "nebo" nevyhovující ".

 V případě výběru porovná celé slovo. v oknech **výsledků hledání** se zobrazí pouze instance **hledaného řetězce,** které odpovídají úplným slovům. Například hledání "CMyObject" vrátí "" ", ale ne" "nebo" MyObjectC ".

 Použijte regulární výrazy, pokud je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu v textových polích **Najít** nebo **nahradit** . Seznam těchto zápisů naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Podívejte se na tyto typy souborů: Tento seznam uvádí typy souborů, které se mají hledat v adresářích **Hledat v** adresáři. Pokud toto pole zůstane prázdné, prohledávají se všechny soubory v adresářích **Hledat v** adresáři.

 Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný hledaný řetězec, ve kterém budou nalezeny soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledku
 Oddíl **možností výsledků** můžete rozbalit nebo sbalit. Můžete vybrat nebo vymazat následující možnosti:

 Pokud je vybráno okno výsledky hledání 1, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 1** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 1**.

 Pokud je vybráno okno výsledky hledání 2, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 2** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 2**.

 Zobrazit názvy souborů jenom v případě, že je toto políčko zaškrtnuté, zobrazí se v oknech výsledků hledání úplná jména a cesty pro všechny soubory, které obsahují hledaný řetězec. Výsledky však neobsahují řádek kódu, kde se zobrazí řetězec. Toto zaškrtávací políčko je k dispozici pouze pro hledání v souborech.

 Ponechat změněné soubory otevřené po tom, co je vybrané, ponechá otevřené všechny soubory, ve kterých byly náhrady provedeny, takže můžete změny vrátit zpět nebo Uložit. Omezení paměti mohou omezit počet souborů, které mohou zůstat otevřeny po operaci Replace.

> [!CAUTION]
> Můžete použít možnost **vrátit zpět** pouze u souborů, které zůstávají otevřené pro úpravy. Pokud tato možnost není vybraná, zůstanou soubory, které ještě nejsou otevřené pro úpravy, zavřené a v těchto souborech nebudou k dispozici žádné možnosti pro **vrácení zpět** .

## <a name="see-also"></a>Viz také
 [Hledání a nahrazování textu](../ide/finding-and-replacing-text.md) [najít v souborech](../ide/find-in-files.md) [Visual Studio Commands](../ide/reference/visual-studio-commands.md)

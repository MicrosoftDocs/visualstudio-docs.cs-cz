---
title: Najít a nahradit v souborech
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585623"
---
# <a name="replace-in-files"></a>Nahradit v souborech

Možnost **nahradit v souborech** umožňuje vyhledat v kódu zadanou sadu souborů pro řetězec nebo výraz a změnit některé nebo všechny nalezené shody. Nalezené shody a podniknuté akce jsou uvedeny v okně **výsledky hledání** vybrané v **Možnosti výsledek**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v **nápovědě** v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, například **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje**  >  **Nastavení importu a exportu**a pak zvolte možnost **resetovat všechna nastavení**.

Pomocí kterékoli z následujících metod můžete v okně **Najít a nahradit** zobrazit **nahradit v souborech** .

## <a name="to-display-replace-in-files"></a>Zobrazení nahrazení v souborech

1. V nabídce **Upravit** rozbalte **Najít a nahradit**.

2. **V souborech vyberte nahradit**.

   ani

   Pokud je okno **Najít a nahradit** již otevřeno, na panelu nástrojů vyberte **nahradit v souborech**.

## <a name="find-what"></a>Najít

Pokud chcete vyhledat nový textový řetězec nebo výraz, zadejte ho do pole. Pokud chcete vyhledat kterýkoli z 20 řetězců, které jste prohledali naposledy, otevřete rozevírací seznam a vyberte řetězec. Pokud chcete v hledaném řetězci použít jeden nebo více regulárních výrazů, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Tlačítko **Tvůrce výrazů** bude povoleno pouze v případě, že jste vybrali možnost **použít regulární výrazy** v části **Možnosti hledání**.

## <a name="replace-with"></a>Nahradit hodnotou

Chcete-li nahradit výskyty řetězce v poli **Najít** s jiným řetězcem, zadejte v poli **Nahradit za** řetězec pro nahrazení. Pokud chcete odstranit instance řetězce v poli **Najít** , ponechte toto pole prázdné. Otevřete seznam pro zobrazení 20 řetězců, pro které jste prohledali poslední. Pokud chcete použít jeden nebo více regulárních výrazů v řetězci pro nahrazení, vyberte tlačítko Tvůrce sousedících **výrazů** . Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Oblast hledání

Možnost zvolená v rozevíracím seznamu **Hledat v** souboru určuje, zda funkce **nahradit v souborech** vyhledává pouze aktuálně aktivní soubory, nebo prohledává všechny soubory uložené v určitých složkách. V seznamu vyberte obor vyhledávání, zadejte cestu ke složce nebo klikněte na tlačítko **Procházet (...)** a zobrazte dialogové okno **Zvolit složky výsledků hledání** a zvolte sadu složek, které chcete vyhledat. Můžete také zadat cestu přímo do pole **Hledat v** .

> [!NOTE]
> Pokud vybraná možnost **Hledat v** způsobí hledání souboru, který jste si rezervovali ze správy zdrojového kódu, prohledává se jenom verze tohoto souboru, který se stáhl do místního počítače.

## <a name="find-options"></a>Možnosti hledání

Můžete rozbalit nebo sbalit část **Možnosti hledání** . Můžete vybrat nebo vymazat následující možnosti:

**Rozlišovat velikost písmen**

Pokud je tato možnost vybrána, okna **výsledků hledání** budou zobrazovat pouze výskyty řetězce **find** , který odpovídá jak podle obsahu, tak i podle velikosti písmen. Například hledání typu "" v "s vybraným **případem shody** vrátí" "", ale ne "", "nebo" nevyhovující ".

**Vyhledat celé slovo**

Když se tato možnost vybere, zobrazí se v oknech **výsledků hledání** jenom **instance hledaného řetězce,** které odpovídají úplným slovům. Například hledání "CMyObject" vrátí "" ", ale ne" "nebo" MyObjectC ".

**Použití regulárních výrazů**

Pokud je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu v textových polích **Najít** nebo **nahradit** . Seznam těchto zápisů naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Podívejte se na tyto typy souborů.**

Tento seznam uvádí typy souborů, které se mají hledat v adresářích **Hledat v** . Pokud toto pole zůstane prázdné, prohledávají se všechny soubory v adresářích **Hledat v** adresáři. Vyberte libovolnou položku v seznamu a zadejte předkonfigurovaný hledaný řetězec, ve kterém budou nalezeny soubory těchto konkrétních typů.

## <a name="result-options"></a>Možnosti výsledku

Oddíl **možností výsledků** můžete rozbalit nebo sbalit. Můžete vybrat nebo vymazat následující možnosti:

Okno **výsledky hledání 1**

Pokud je tato možnost vybrána, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 1** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 1**.

Okno **výsledky hledání 2**

Pokud je tato možnost vybrána, nahradí výsledky aktuálního hledání obsah okna **výsledky hledání 2** . Toto okno se automaticky otevře, aby se zobrazily výsledky hledání. Chcete-li toto okno otevřít ručně, v nabídce **zobrazení** vyberte možnost **Další okna** a zvolte možnost **Najít výsledky 2**.

**Zobrazit pouze názvy souborů**

Když je toto políčko zaškrtnuté, zobrazí se v oknech **výsledků hledání** celá jména a cesty pro všechny soubory, které obsahují hledaný řetězec. Výsledky však neobsahují řádek kódu, kde se zobrazí řetězec. Toto zaškrtávací políčko je k dispozici pouze pro **hledání v souborech** .

**Ponechat změněné soubory otevřené po nahrazení vše**

Když se tato možnost vybere, ponechá otevřené všechny soubory, ve kterých byly náhrady provedeny, takže můžete změny vrátit zpět nebo Uložit. Omezení paměti mohou omezit počet souborů, které mohou zůstat otevřeny po operaci Replace.

> [!CAUTION]
> Můžete použít možnost **vrátit zpět** pouze u souborů, které zůstávají otevřené pro úpravy. Pokud tato možnost není vybraná, zůstanou soubory, které ještě nejsou otevřené pro úpravy, zavřené a v těchto souborech nebudou k dispozici žádné možnosti pro **vrácení zpět** .

## <a name="see-also"></a>Viz také

- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
- [Najít v souborech](../ide/find-in-files.md)
- [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)

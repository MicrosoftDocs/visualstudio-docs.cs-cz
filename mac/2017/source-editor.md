---
title: Editor zdroje
description: Použití zdrojového editoru ve Visual Studiu pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985214"
---
# <a name="source-editor"></a>Zdrojový editor

Spolehlivý zdrojový editor je nezbytný pro stručné a efektivní psaní kódu. Visual Studio pro Mac poskytuje sofistikovaný zdrojový editor, který je ve středu vašich interakcí s rozhraním IDE. Zdrojový editor poskytuje funkce, které můžete očekávat a je třeba dělat svou práci s lehkostí: Od základů, jako je zvýraznění syntaxe, fragmenty kódu a skládání kódu, až po výhody integrace kompilátoru Roslyn, jako je plně funkční kód IntelliSense Dokončení.

Zdrojový editor v sadě Visual Studio for Mac umožňuje bezproblémové prostředí se všemi ostatními funkcemi v rozhraní IDE, jako je ladění, refaktoring a integrace správy verzí.

Tento článek představuje některé klíčové funkce zdrojového editoru a zkoumá, jak můžete použít Visual Studio pro Mac, aby bylo co nejproduktivnější.

## <a name="the-source-editor-experience"></a>Prostředí editoru zdroje

Efektivní prohlížení a přesouvání v rámci kódu je nedílnou součástí pracovního postupu vývoje. Přesně tak, jak se rozhodnete zobrazit a udržovat kód je osobní rozhodnutí, které se liší mezi vývojáři - a často mezi projekty.

Visual Studio pro Mac nabízí mnoho výkonných funkcí, které usnadňují vývoj napříč platformami a co nejužitečnější. Následující části popisují některé z nejdůležitějších bodů.

## <a name="code-folding"></a>Skrytí kódu

Skládání kódu usnadňuje správu velkých souborů zdrojového kódu tím, že vývojářům umožňuje zobrazit nebo skrýt úplné části kódu, například pomocí direktiv, často používaný kód a komentáře a #region příkazy. Skládání kódu je ve výchozím nastavení ve Visual Studiu pro Mac vypnuté

Pokud chcete zapnout skládání kódu, přejděte **na > předvolby > textového editoru > obecné > skládání kódu**:

![Možnosti skládání kódu](media/source-editor-image1.png)

Tato nabídka také obsahuje možnost překládat #regions a komentáře ve výchozím nastavení, zobrazení pojmenované nápovědy, místo kódu.

Chcete-li zobrazit nebo skrýt oddíly, použijte widget zveřejnění vedle čísla řádku:

![Zobrazení nebo skrytí oddílů v kódu](media/source-editor-image2.png)

Můžete také přepínat mezi zobrazením a skrytím záhybů pomocí položky nabídky **View > Folding > Přepnout přeložení / přepnout všechny záhyby:**

![Položka skládací nabídky](media/source-editor-image19.png)

Tuto položku nabídky lze také použít k povolení nebo zakázání skládání kódu.

## <a name="white-space"></a>Prázdné místo

Může být nutné zobrazit neviditelné znaky ve zdrojovém kódu. Je to viditelný způsob, jak se ujistit, že jste dodržování standardů kódování a není zbytečně ztrácet místo. Je také užitečné při psaní F#, který závisí na přesně odsazené řádky pro vyhodnocení kódu.

Nastavte možnosti zobrazení prázdného místa přechodem na **předvolby > sady Visual Studio > textový editor > značek a pravítek**. Výběr této volby umožňuje _nastavení, kdy_ se zobrazí neviditelné znaky: Nikdy, Při výběru nebo Vždy:

![Zobrazit volby neviditelných znaků](media/source-editor-image3.png)

K dispozici je také možnost zobrazení karet, mezer a zakončení řádků:

![Zobrazení karet a mezer](media/source-editor-image4.png)

Neviditelné znaky jsou zobrazeny jako šedé tečky, jak je znázorněno na následujícím obrázku:

![zobrazeny prázdné znaky](media/source-editor-image22.png)

## <a name="ruler"></a>Pravítko

Pravítko sloupce je užitečné pro určení délek čar, zejména při práci s týmem, který má vodítka délky čáry. Pravítko sloupce lze zapnout nebo vypnout tak, že přejdete do **předvoleb sady Visual Studio > > textový editor > značky a pravítka a** vyberete (nebo odznačíte) **zobrazení pravítka sloupce,** jak je znázorněno na následujícím obrázku:

![Dialogové okno Předvolby se zvýrazněným zobrazením pravítka sloupců](media/source-editor-image5.png)

 Zobrazí se jako svislá světle šedá čára ve zdrojovém editoru.

## <a name="highlight-identifier-references"></a>Zvýraznit odkazy na identifikátory

S možností "Zvýraznit odkazy na identifikátory" můžete vybrat libovolný symbol ve zdrojovém kódu a zdrojový editor poskytne vizuální průvodce pro všechny ostatní odkazy v tomto souboru. Chcete-li tuto možnost zapnout, přejděte na **předvolby sady Visual Studio > > textový editor > značky a pravítka** a vyberte _odkazy na identifikátory zvýraznění_, jak je znázorněno na následujícím obrázku:

![Dialogové okno Předvolby se zvýrazněnou možností Zvýraznit odkazy na identifikátory](media/source-editor-image6.png)

Barva zvýraznění je také užitečná pro označující, že něco je přiřazeno nebo odkazováno. Pokud je něco přiřazeno, je zvýrazněno červeně; pokud je odkazováno, je zvýrazněno modře:

![příklad znázorňující barvu zvýraznění](media/source-editor-image7.png)

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu (Visual Studio ve Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Osnova (Visual Studio ve Windows)](/visualstudio/ide/outlining)
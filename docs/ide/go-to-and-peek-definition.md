---
title: Zobrazení definic typů
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7b159eb48e995fa0bca6ea86299d09c1a10cf27
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062079"
---
# <a name="view-type-and-member-definitions"></a>Zobrazení definic typů a členů

Vývojáři často potřebují zobrazit zdrojový kód definice pro typy nebo členy třídy, které používají ve svém kódu. V sadě Visual Studio **přejít k definici** a **definice operace Peek** funkce umožňují snadno zobrazit definice typu nebo členu. Pokud není k dispozici zdrojový kód, zobrazí se místo toho metadat.

## <a name="go-to-definition"></a>Přejít k definici

**Přejít k definici** funkce přejde na zdroj typ nebo člen a výsledek se otevře v nové záložce. Pokud jste uživatelem klávesnice, umístit textový kurzor někam název symbolu a stiskněte klávesu **F12**. Pokud jste uživatelem myši, vyberte buď **přejít k definici** z místní nabídky nebo použití **klávesou Ctrl** funkcí popsaných v následující části.

### <a name="ctrl-click-go-to-definition"></a>Klávesou CTRL přejít k definici

V sadě Visual Studio 2017 verze 15.4, je pro uživatele myši snadný způsob, jak rychle přístup **přejít k definici**. Symboly se po kliknutí, když stisknete klávesu **Ctrl** a podržte ukazatel myši nad tento typ nebo člen. Chcete-li rychle přejít k definici symbolu, stiskněte **Ctrl** klíče a pak klikněte na něj. Je to snadné!

![Přejít na definici animace kliknutí myší](../ide/media/click_gotodef.gif)

Modifikační klávesy pro kliknutí myši můžete změnit **přejít k definici** tak, že přejdete do **nástroje** > **možnosti** > **textový Editor**   >  **Obecné**a výběru **Alt** nebo **Ctrl + Alt** z **použít modifikátor klíč**rozevíracího seznamu. Můžete také zakázat kliknutí myší **přejít k definici** zrušením **povolit kliknutí myši provedení přejít k definici** zaškrtávací políčko.

![Povolení kliknutí myší přejít k definici](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Náhled definice

**Definice operace Peek** funkce umožňuje zobrazit náhled definice typu, aniž byste museli opustit aktuální umístění v editoru. Pokud jste uživatelem klávesnice, umístit textový kurzor někam typ nebo člen název a stiskněte klávesu **Alt + F12**. Pokud jste uživatel myší, můžete si vybrat **definice operace Peek** v místní nabídce. V sadě Visual Studio 2017 verze 15.4 nebo novější je nový způsob zobrazení náhledu definice pomocí myši. Nejprve přejděte na **nástroje** > **možnosti** > **textový Editor** > **Obecné**. Vyberte možnost **Otevřít definici v zobrazení náhledu** a klikněte na tlačítko **OK** zavřete **možnosti** dialogové okno.

![Nastavení možnosti kliknutí myší funkce Náhled definice](../ide/media/editor_options_peek_view.png)

Poté stiskněte **Ctrl** (nebo libovolným modifikační klávesa je vybrán v **možnosti**) a klikněte na tento typ nebo člen.

![Náhled definice animace](../ide/media/peek_definition.gif)

Pokud jste náhled jiné definice v automaticky otevíraném okně, se spustí navigace s popisem cesty cestu, která můžete procházet pomocí kruhů a šipky, které se zobrazují nad automaticky otevírané okno.

Další informace najdete v tématu [postupy: zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Zobrazování metadat ve formě zdrojového kódu (C#)

Při prohlížení definici C# typy nebo členy, jejíž zdrojový kód není k dispozici, se místo toho zobrazí jejich metadat. Zobrazí se deklarace typů a členů, ale ne jejich implementace.

Při spuštění **přejít k definici** nebo **definice operace Peek** příkaz pro některou položku, jejíž zdrojový kód je k dispozici, dokument s kartami, který obsahuje zobrazení metadat danou položku, zobrazí jako zdrojový kód, Zobrazí se v editoru kódu. Název typu, následovaný **[z metadat]**, se zobrazí na kartě dokumentu.

Například pokud spustíte **přejít k definici** příkazu <xref:System.Console>, metadata pro <xref:System.Console> se zobrazí v editoru kódu jako C# zdrojový kód. Kód se podobá jeho deklaraci, ale nezobrazuje implementace.

![Metadata jako zdroj](../ide/media/metadatasource.png)

> [!NOTE]
> Při pokusu o spuštění **přejít k definici** nebo **definice operace Peek** příkaz pro typy nebo členy, které jsou označeny jako vnitřní, Visual Studio nezobrazuje jako zdrojový kód, bez ohledu na to, zda jejich metadat odkazující sestavení je přítele či nikoli.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Zobrazit definice dekompilované zdroje místo metadata (C#)

Nový v sadě Visual Studio 2017 verze 15.6 můžete nastavit možnost pro zobrazení dekompilované zdrojového kódu, když zobrazujete definici C# typ nebo člen, jejíž zdrojový kód je k dispozici. Chcete-li tuto funkci zapnout, zvolte **nástroje** > **možnosti** z řádku nabídek. Pak rozbalte **textový Editor** > **C#** > **Upřesnit**a vyberte **povolit navigaci na dekompilované zdroje** .

![Zobrazení dekompilované definice](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje těl metod pomocí dekompilace ILSpy. Při prvním přístupu k této funkci, musíte souhlasit s právní omezení týkající se softwaru správy licencí a o autorských právech a trademark zákony.

## <a name="see-also"></a>Viz také:

- [Vyhledání kódu](../ide/navigating-code.md)
- [Postupy: zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
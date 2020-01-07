---
title: Zobrazení definic typů
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592071"
---
# <a name="view-type-and-member-definitions"></a>Zobrazení definic typů a členů

Vývojáři často potřebují zobrazit zdrojový kód definice pro typy nebo členy třídy, které používají ve svém kódu. V sadě Visual Studio **přejít k definici** a **definice operace Peek** funkce umožňují snadno zobrazit definice typu nebo členu. Pokud není k dispozici zdrojový kód, zobrazí se místo toho metadat.

## <a name="go-to-definition"></a>Přejít k definici

Funkce **Přejít k definici** přejde ke zdroji typu nebo členu a otevře výsledek na nové kartě. Pokud jste uživatel klávesnice, umístěte textový kurzor do názvu symbolu a stiskněte klávesu **F12**. Pokud jste uživatel myši, vyberte možnost **Přejít k definici** z nabídky po kliknutí pravým tlačítkem myši nebo použijte funkci se **stisknutou klávesou Ctrl** popsanou v následující části.

### <a name="ctrl-click-go-to-definition"></a>Klávesou CTRL přejít k definici

**Ctrl**+**klikněte na** klávesovou zkratku pro uživatele myši k rychlému přístupu **Přejít k definici**. Symboly se po kliknutí, když stisknete klávesu **Ctrl** a podržte ukazatel myši nad tento typ nebo člen. Chcete-li rychle přejít k definici symbolu, stiskněte **Ctrl** klíče a pak klikněte na něj. Je to snadné!

![Přejít na definici animace kliknutí myší](../ide/media/click_gotodef.gif)

Můžete změnit modifikační klávesu pro myš – klikněte na **Přejít k definici** tak, že přejdete na **nástroje** > **Možnosti** > **textový editor** > **Obecné**a v rozevíracím seznamu **použít klávesu** ALT vyberete buď **ALT** , nebo **CTRL**+**ALT** . Můžete také zakázat kliknutí myší **přejít k definici** zrušením **povolit kliknutí myši provedení přejít k definici** zaškrtávací políčko.

![Povolení kliknutí myší přejít k definici](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Náhled definice

**Definice operace Peek** funkce umožňuje zobrazit náhled definice typu, aniž byste museli opustit aktuální umístění v editoru. Pokud jste uživatelem klávesnice, umístit textový kurzor někam typ nebo člen název a stiskněte klávesu **Alt + F12**. Pokud jste uživatelem myši, můžete v nabídce kliknutím pravým tlačítkem vybrat možnost **Náhled definice** .

Pokud chcete povolit funkci **Ctrl**+**kliknutí** , přejděte na **nástroje** > **Možnosti** > **textový editor** > **Obecné**. Vyberte možnost **Otevřít definici v zobrazení náhledu** a klikněte na tlačítko **OK** zavřete **možnosti** dialogové okno.

![Nastavení možnosti kliknutí myší funkce Náhled definice](../ide/media/editor_options_peek_view.png)

Poté stiskněte **Ctrl** (nebo libovolným modifikační klávesa je vybrán v **možnosti**) a klikněte na tento typ nebo člen.

![Náhled definice animace](../ide/media/peek_definition.gif)

Pokud si z překryvného okna zobrazíte další definici, spustíte cestu s popisem cesty, pomocí které můžete procházet kružnice a šipky, které se zobrazí nad automaticky otevírané okno.

Další informace najdete v tématu [postupy: zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Zobrazování metadat ve formě zdrojového kódu (C#)

Při prohlížení definici C# typy nebo členy, jejíž zdrojový kód není k dispozici, se místo toho zobrazí jejich metadat. Zobrazí se deklarace typů a členů, ale ne jejich implementace.

Při spuštění **přejít k definici** nebo **definice operace Peek** příkaz pro některou položku, jejíž zdrojový kód je k dispozici, dokument s kartami, který obsahuje zobrazení metadat danou položku, zobrazí jako zdrojový kód, Zobrazí se v editoru kódu. Název typu, následovaný **[z metadat]** , se zobrazí na kartě dokumentu.

Například pokud spustíte **přejít k definici** příkazu <xref:System.Console>, metadata pro <xref:System.Console> se zobrazí v editoru kódu jako C# zdrojový kód. Kód se podobá jeho deklaraci, ale nezobrazuje implementace.

![Metadata jako zdroj](../ide/media/metadatasource.png)

> [!NOTE]
> Při pokusu o spuštění **přejít k definici** nebo **definice operace Peek** příkaz pro typy nebo členy, které jsou označeny jako vnitřní, Visual Studio nezobrazuje jako zdrojový kód, bez ohledu na to, zda jejich metadat odkazující sestavení je přítele či nikoli.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Zobrazit definice dekompilované zdroje místo metadata (C#)

Můžete nastavit možnost Zobrazit dekompilovaný zdrojový kód při zobrazení definice C# typu nebo člena, jehož zdrojový kód není k dispozici. Chcete-li tuto funkci zapnout, zvolte **nástroje** > **možnosti** z řádku nabídek. Pak rozbalte **textový Editor** > **C#**  > **Upřesnit**a vyberte **povolit navigaci na dekompilované zdroje** .

![Zobrazení dekompilované definice](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje těl metod pomocí dekompilace ILSpy. Při prvním přístupu k této funkci, musíte souhlasit s právní omezení týkající se softwaru správy licencí a o autorských právech a trademark zákony.

## <a name="see-also"></a>Viz také:

- [Vyhledání kódu](../ide/navigating-code.md)
- [Postupy: zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

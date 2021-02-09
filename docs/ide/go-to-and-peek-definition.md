---
title: Zobrazení definic typů
description: Přečtěte si o funkcích přejít na definici a náhled definice, které vám umožní snadno zobrazit definici typu nebo člena.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 804c49c079f619a774cb1f99d54b2b2af5a3929d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869359"
---
# <a name="view-type-and-member-definitions"></a>Zobrazení definic typů a členů

Vývojáři často potřebují zobrazit definice zdrojového kódu pro typy nebo členy třídy, které používají ve svém kódu. V aplikaci Visual Studio umožňují funkce **Přejít k** definici a **Náhled definice** snadno zobrazit definici typu nebo člena. Pokud není zdrojový kód k dispozici, zobrazí se místo toho metadata.

## <a name="go-to-definition"></a>Přejít k definici

Funkce **Přejít k definici** přejde ke zdroji typu nebo členu a otevře výsledek na nové kartě. Pokud jste uživatel klávesnice, umístěte textový kurzor do názvu symbolu a stiskněte klávesu **F12**. Pokud jste uživatel myši, vyberte možnost **Přejít k definici** z nabídky po kliknutí pravým tlačítkem myši nebo použijte funkci se **stisknutou klávesou Ctrl** popsanou v následující části.

### <a name="ctrl-click-go-to-definition"></a>Ctrl + kliknutí přejít k definici

**CTRL** + **klikněte na** klávesovou zkratku pro uživatele myši k rychlému přístupu **Přejít k definici**. Když stisknete **klávesu CTRL** a najedete myší na daný typ nebo člen, symboly se stanou kliknutím. Pokud chcete rychle přejít k definici symbolu, stiskněte klávesu **CTRL** a pak na ni klikněte. Tak je to snadné!

![Myš kliknutí na přejít k definici animace](../ide/media/click_gotodef.gif)

Můžete změnit modifikační klávesu pro myš – klikněte na **Přejít k definici** tak, že přejdete do části **nástroje**  >  **Možnosti**  >  **textový editor**  >  **Obecné** a v   + rozevíracím seznamu **použít klávesu pro použití modifikátoru** vyberte ALT nebo CTRL **ALT** . Můžete také zakázat myš – klikněte na **Přejít k definici** tím, že zrušíte zaškrtnutí políčka **Povolit možnost přejít k definici** .

![Povolení kliknutí myší na položku Přejít k definici](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Náhled definice

Funkce **Náhled definice** umožňuje zobrazit náhled definice typu bez nutnosti opustit aktuální umístění v editoru. Pokud jste uživatel klávesnice, umístěte textový kurzor do pole typ nebo název členu a stiskněte klávesy **Alt + F12**. Pokud jste uživatelem myši, můžete v nabídce kliknutím pravým tlačítkem vybrat možnost **Náhled definice** .

Chcete-li povolit funkce **stisknutí klávesy CTRL** +  , přejděte do možnosti **nástroje**  >    >  **textový editor**  >  **Obecné**. **V zobrazení Náhled vyberte možnost otevřená definice** a kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti** .

![Nastavení možnosti Náhled definice v nabídce myši](../ide/media/editor_options_peek_view.png)

Pak stiskněte klávesu **CTRL** (nebo se v **možnostech** vybere jakákoli modifikační klávesa) a klikněte na typ nebo člen.

![Animace náhledu definice](../ide/media/peek_definition.gif)

Pokud si z překryvného okna zobrazíte další definici, spustíte cestu s popisem cesty, pomocí které můžete procházet kružnice a šipky, které se zobrazí nad automaticky otevírané okno.

Další informace najdete v tématu [Postup: zobrazení a úpravy kódu pomocí funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Zobrazit metadata jako zdrojový kód (C#)

Pokud zobrazíte definici typů nebo členů jazyka C#, jejichž zdrojový kód není k dispozici, zobrazí se místo nich jejich metadata. Můžete zobrazit deklarace typů a členů, ale ne jejich implementace.

Když spustíte příkaz **Přejít na definici** nebo **Náhled definice** pro položku, jejíž zdrojový kód není k dispozici, dokument s kartami, který obsahuje zobrazení metadat této položky, zobrazený jako zdrojový kód, se zobrazí v editoru kódu. Název typu, za nímž následuje **[from metadata]**, se zobrazí na kartě dokumentu.

Například pokud spustíte příkaz **Přejít na definici** pro <xref:System.Console> , <xref:System.Console> zobrazí se metadata v editoru kódu jako zdrojový kód C#. Kód se podobá deklaraci, ale nezobrazuje implementaci.

![Metadata jako zdroj](../ide/media/metadatasource.png)

> [!NOTE]
> Když se pokusíte spustit příkaz **Přejít k definici** nebo **Náhled definice** pro typy nebo členy, které jsou označeny jako interní, Visual Studio nezobrazuje své metadata jako zdrojový kód, bez ohledu na to, zda odkazující sestavení je přítel nebo ne.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Zobrazit dekompilované definice zdrojů namísto metadat (C#)

Můžete nastavit možnost Zobrazit dekompilovaný zdrojový kód při zobrazení definice typu nebo členu jazyka C#, jehož zdrojový kód není k dispozici. Pokud chcete tuto funkci zapnout, na   >  panelu nabídek vyberte **Možnosti** nástrojů. Pak rozbalte položku **textový editor**  >  **C#**  >  **Upřesnit** a vyberte možnost **Povolit navigaci na dekompilované zdroje**.

![Zobrazení definice dekompilovaných](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje tělo metody pomocí ILSpy dekompilace. Při prvním přístupu k této funkci musíte souhlasit s právním omezením týkajícím se licencování softwaru a autorských práv a ochranných známek.

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
- [Postupy: zobrazení a úpravy kódu pomocí funkce Náhled definice (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

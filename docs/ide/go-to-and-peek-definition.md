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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592071"
---
# <a name="view-type-and-member-definitions"></a>Zobrazení definic typů a členů

Vývojáři často potřebují zobrazit definice zdrojového kódu pro typy nebo členy třídy, které používají ve svém kódu. V sadě Visual Studio umožňují funkce **Přejít na definici** a **náhled** snadno zobrazit definici typu nebo člena. Pokud zdrojový kód není k dispozici, zobrazí se místo toho metadata.

## <a name="go-to-definition"></a>Přejít na definici

Funkce **Přejít na definici** přejde ke zdroji typu nebo člena a otevře výsledek na nové kartě. Pokud jste uživatel klávesnice, umístěte textový kurzor někde uvnitř názvu symbolu a stiskněte **klávesu F12**. Pokud jste uživatel myši, vyberte v nabídce pravým tlačítkem myši možnost **Přejít na definici** nebo použijte funkci **se stisknutou klávesou Ctrl** popsanou v následující části.

### <a name="ctrl-click-go-to-definition"></a>Ctrl-klepnout na Přejít na definici

**Ctrl**+**click** je zkratka pro uživatele myši pro rychlý přístup **k definici přejít na .** Symboly se stanou klikacími, když stisknete **klávesu Ctrl** a najedete na text nebo člen. Chcete-li rychle přejít na definici symbolu, stiskněte klávesu **Ctrl** a klikněte na ni. Je to tak snadné!

![Kliknutím myši přejdete na animaci definic](../ide/media/click_gotodef.gif)

Modifikátor klávesy pro přechod na **definici** kliknutím myši můžete změnit tak, že přejdete na**Options** > **Texteditor** >  **u nástrojů** > **– obecné**a v rozevíracím seznamu **Použít modifikační klávesu** vyberete **alt** nebo **ctrl**+**Alt** alt. Můžete také zakázat klepnutí myší na **přejít na definici** zrušením zaškrtnutí políčka **Povolit klepnutí myší na provedení příkazu Přejít na definici.**

![Povolení klepnutí myší přejít na definici](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Náhled definice

Funkce **Definice náhledu** umožňuje zobrazit náhled definice typu, aniž byste opustili aktuální umístění v editoru. Pokud jste uživatel klávesnice, umístěte textový kurzor někde uvnitř textového nebo členského jména a stiskněte **klávesu Alt + F12**. Pokud jste uživatel myši, můžete v nabídce po kliknutí pravým tlačítkem myši vybrat **možnost Definice náhledu.**

Chcete-li povolit funkci**klepnutí** **na klávesu Ctrl,**+přejděte na**obecné editor****textových editorů** > **možností** >  **nástrojů** > . Vyberte volbu **Otevřít definici v náhledovém zobrazení** a klepnutím na **OK** zavřete dialogové okno **Volby.**

![Nastavení možnosti definice náhledu klepnutím myši](../ide/media/editor_options_peek_view.png)

Potom stiskněte **kombinaci kláves (nebo** libovolné modifikační klávesy v **části Možnosti**) a klikněte na typ nebo člen.

![Animace definice náhledu](../ide/media/peek_definition.gif)

Pokud se podíváte na jinou definici z vyskakovacího okna, spustíte cestu s popisem cesty, kterou můžete procházet pomocí kruhů a šipek, které se zobrazují nad vyskakovacím oknem.

Další informace naleznete v [tématu How to: View and edit code pomocí Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Zobrazit metadata jako zdrojový kód (C#)

Při zobrazení definice c# typy nebo členy, jejichž zdrojový kód není k dispozici, jejich metadata se zobrazí místo. Můžete zobrazit deklarace typů a členů, ale ne jejich implementace.

Při spuštění příkazu **Přejít na definici** nebo **definici náhledu** pro položku, jejíž zdrojový kód není k dispozici, se v editoru kódu zobrazí dokument s kartami, který obsahuje zobrazení metadat této položky zobrazené jako zdrojový kód. Název typu následovaný **[z metadat]** se zobrazí na kartě dokumentu.

Pokud například spustíte příkaz **Přejít na definici** pro <xref:System.Console>, metadata pro <xref:System.Console> se zobrazí v editoru kódu jako zdrojový kód Jazyka C#. Kód se podobá jeho deklaraci, ale nezobrazuje implementaci.

![Metadata jako zdroj](../ide/media/metadatasource.png)

> [!NOTE]
> Při pokusu o spuštění příkazu **Přejít na definici** nebo **náhled definice** pro typy nebo členy, které jsou označeny jako interní, Visual Studio nezobrazí jejich metadata jako zdrojový kód, bez ohledu na to, zda odkazující sestavení je přítel nebo ne.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Zobrazit dekompilované zdrojové definice místo metadat (C#)

Můžete nastavit možnost zobrazit dekompilovaný zdrojový kód při zobrazení definice typu C# nebo člena, jehož zdrojový kód není k dispozici. Chcete-li tuto funkci zapnout, zvolte**Možnosti** **nástrojů** > z panelu nabídek. Potom rozbalte **text editor c#** > **C#** > **Upřesnit**a vyberte **Povolit navigaci dekompilované zdroje**.

![Zobrazení dekompilované definice](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje těla metod pomocí ILSpy dekompilace. Při prvním přístupu k této funkci musíte souhlasit s právním prohlášením o udělení odpovědnosti v souvislosti se zákonem o licencování softwaru a autorských právech a ochranných známkách.

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
- [Postup: Zobrazení a úprava kódu pomocí definice náhledu (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

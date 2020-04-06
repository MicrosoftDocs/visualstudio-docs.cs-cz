---
title: Přidání ikon do příkazů nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740150"
---
# <a name="add-icons-to-menu-commands"></a>Přidání ikon do příkazů nabídky
Příkazy se mohou zobrazit v nabídkách i panelech nástrojů. Na panelech nástrojů je běžné, že příkaz se zobrazí pouze s ikonou (pro úsporu místa), zatímco v nabídkách se příkaz obvykle zobrazí s ikonou i textem.

 Ikony jsou 16 pixelů široké a 16 pixelů vysoké a mohou být buď 8bitová barevná hloubka (256 barev) nebo 32bitová barevná hloubka (skutečná barva). Upřednostňovány jsou 32bitové ikony barev. Ikony jsou obvykle uspořádány do jednoho vodorovného řádku v jedné bitmapě, i když je povoleno více bitmap. Tato bitmapa je deklarována v souboru *.vsct* spolu s jednotlivými ikonami dostupnými v bitmapě. Další podrobnosti najdete v odkazu na [element Bitmaps.](../extensibility/bitmaps-element.md)

## <a name="add-an-icon-to-a-command"></a>Přidání ikony do příkazu
 Následující postup předpokládá, že máte existující projekt VSPackage s příkazem nabídky. Informace o tom, jak to provést, naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Vytvořte bitmapu s barevnou hloubkou 32 bitů. Ikona je vždy 16 x 16, takže tato bitmapa musí být 16 pixelů vysoká a násobkem 16 pixelů široký.

     Každá ikona je umístěna na bitmapu vedle sebe v jednom řádku. Alfa kanál slouží k označení míst průhlednosti v každé ikoně.

     Pokud používáte 8bitovou barevnou hloubku, `RGB(255,0,255)`použijte jako průhlednost purpurovou , . Jsou však upřednostňovány 32bitové ikony barev.

2. Zkopírujte soubor ikony do *adresáře Zdroje* v projektu VSPackage. V **Průzkumníku řešení**přidejte ikonu do projektu. (Vyberte **Zdroje**a v místní nabídce klepněte na tlačítko **Přidat**, potom na **položku Existující**a vyberte soubor ikon.)

3. Otevřete soubor *.vsct* v editoru.

4. Přidejte `GuidSymbol` prvek s názvem **testIcon**. Vytvořte identifikátor GUID **(Nástroje** > **vytvářejí identifikátor GUID**, vyberte možnost Formát **registru** a klepněte na **kopírovat**) a vložte jej do atributu. `value` Výsledek by měl vypadat takto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Přidejte `<IDSymbol>` ikonu pro. Atributem `name` je ID ikony a `value` označuje jeho umístění na proužku, pokud existuje. Pokud existuje pouze jedna ikona, přidejte 1. Výsledek by měl vypadat takto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Vytvořte `<Bitmap>` v `<Bitmaps>` části souboru *.vsct,* která představuje bitmapu obsahující ikony.

    - Nastavte `guid` hodnotu na název `<GuidSymbol>` prvku, který jste vytvořili v předchozím kroku.

    - Nastavte `href` hodnotu na relativní cestu bitmapového souboru (v tomto případě **zdroje\\<název\>souboru ikony**.

    - Nastavte `usedList` hodnotu na IDSymbol, který jste vytvořili dříve. Tento atribut určuje seznam ikon oddělených čárkami, které mají být použity v balíčku VSPackage. Ikony, které nejsou v seznamu, jsou vyloučeny kompilace formuláře.

         Blok Bitmap by měl vypadat takto:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. V existujícím `<Button>` prvku `Icon` nastavte prvek na hodnoty GUIDSymbol a IDSymbol, které jste vytvořili dříve. Tady je příklad prvku Button s těmito hodnotami:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Otestujte ikonu. Sestavení projektu a začít ladění. V experimentální instanci najděte příkaz. Měla by se zobrazit ikona, kterou jste přidali.

## <a name="see-also"></a>Viz také
- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Odkaz na schéma XML VSCT](../extensibility/vsct-xml-schema-reference.md)

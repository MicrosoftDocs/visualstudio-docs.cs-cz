---
title: Přidávání ikon do příkazů nabídky | Microsoft Docs
description: Naučte se, jak přidat ikony do příkazů, které se mohou objevit v nabídkách a panelech nástrojů v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9f37bd14ed43ab0e165346f8ce09512c3981177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934361"
---
# <a name="add-icons-to-menu-commands"></a>Přidat ikony do příkazů nabídky
Příkazy se můžou objevit v nabídkách i na panelech nástrojů. Na panelech nástrojů je běžné, že se příkaz zobrazí jenom s ikonou (k uložení prostoru), zatímco v nabídkách se příkaz obvykle zobrazuje s ikonou i textem.

 Ikony jsou 16 pixelů v šířce až 16 pixelů vysoké a může se jednat o 8bitové hloubky barev (256 barev) nebo 32 barev hloubkové hloubky (True Color). jsou preferované ikony bitových barev 32. Ikony jsou obvykle uspořádány do jednoho vodorovného řádku v jedné bitmapě, i když je povoleno více rastrových obrázků. Tato bitmapa je deklarována v souboru *. vsct* spolu s jednotlivými ikonami dostupnými v rastrovém obrázku. Další podrobnosti najdete v referenčních informacích k [elementu bitmapy](../extensibility/bitmaps-element.md) .

## <a name="add-an-icon-to-a-command"></a>Přidání ikony do příkazu
 Následující postup předpokládá, že máte existující projekt VSPackage s příkazem nabídky. Další informace o tom, jak to provést, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Vytvořte rastrový obrázek s barevnou hloubkou 32-bitů. Ikona je vždy 16 × 16, takže tento rastrový obrázek musí být o 16 pixelů vysoký a násobkem 16 pixelů na šířku.

     Každá ikona je umístěna na rastrovém obrázku vedle sebe na jednom řádku. Použijte alfa kanál k označení míst průhlednosti v každé ikoně.

     Použijete-li 8bitové hloubku barev, jako průhlednost použijte purpurovou barvu `RGB(255,0,255)` . Nicméně jsou upřednostňovány 32 bitové ikony barev.

2. Zkopírujte soubor ikony do adresáře *prostředků* v projektu VSPackage. V **Průzkumník řešení** přidejte ikonu do projektu. (Vyberte **prostředky** a v místní nabídce klikněte na **Přidat**, pak na **existující položku** a vyberte soubor ikony.)

3. Otevřete soubor *. vsct* v editoru.

4. Přidejte `GuidSymbol` element s názvem **testIcon**. Vytvořte identifikátor GUID (**nástroje**  >  **vytvořit GUID**, pak vyberte **Formát registru** a klikněte **na Kopírovat**) a vložte ho do `value` atributu. Výsledek by měl vypadat takto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Přidejte `<IDSymbol>` pro ikonu. `name`Atribut je ID ikony a `value` označuje jeho polohu na pruhu, pokud existuje. Pokud je k dispozici pouze jedna ikona, přidejte 1. Výsledek by měl vypadat takto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Vytvořte `<Bitmap>` v `<Bitmaps>` části souboru *. vsct* , který bude představovat rastrový obrázek obsahující ikony.

    - Nastavte `guid` hodnotu na název `<GuidSymbol>` prvku, který jste vytvořili v předchozím kroku.

    - Nastavte `href` hodnotu na relativní cestu k souboru rastrového obrázku (v tomto případě **prostředky \\<název \> souboru ikony**.

    - Nastavte `usedList` hodnotu na IDSymbol, kterou jste vytvořili dříve. Tento atribut určuje seznam ikon oddělených čárkami, které mají být použity v VSPackage. Ikony, které nejsou v seznamu, jsou vyloučeny z kompilace.

         Blok rastrového obrázku by měl vypadat takto:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. V existujícím `<Button>` elementu nastavte `Icon` element na hodnoty GUIDSymbol a IDSymbol, které jste vytvořili dříve. Tady je příklad prvku tlačítka s těmito hodnotami:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Otestujte ikonu. Sestavte projekt a spusťte ladění. V experimentální instanci Najděte příkaz. Měla by se zobrazit ikona, kterou jste přidali.

## <a name="see-also"></a>Viz také
- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Referenční dokumentace schématu VSCT XML](../extensibility/vsct-xml-schema-reference.md)

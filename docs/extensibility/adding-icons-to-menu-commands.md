---
title: Přidávání ikon k příkazům nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d01e64915004eb21a92c21a67291dc4f034112d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155008"
---
# <a name="add-icons-to-menu-commands"></a>Přidání ikon k příkazům nabídky
Příkazy se může objevit v nabídek a panelů nástrojů. Na panely nástrojů je běžné, že příkaz zobrazuje jenom ikona (pro úsporu místa) při v nabídkách příkaz obvykle se zobrazí se ikona i text.  
  
 Ikony jsou 16 pixelů na šířku a 16 pixelů a může být 8 bitů barevnou hloubku (256 barev) nebo 32-bit barevnou hloubku (true barvu). 32bitové barvy ikony jsou upřednostňované. Ikony jsou obvykle uspořádány v jediném řádku vodorovné v jediné bitmapě, i když více rastrových obrázků jsou povoleny. Tento rastrový obrázek je deklarován v *.vsct* souboru spolu s jednotlivé ikony rastrového obrázku nastaven k dispozici. Přečtěte si referenční informace pro [bitmaps – element](../extensibility/bitmaps-element.md) další podrobnosti.  
  
## <a name="add-an-icon-to-a-command"></a>Přidání ikony k příkazu  
 Následující postup předpokládá, že máte existující projekt balíčku VSPackage pomocí příkazu nabídky. Zjistěte, jak to udělat, najdete v článku [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Vytvořte rastrový obrázek s barevnou hloubku 32 bitů. Ikona je vždy 16 x 16, takže tento rastrový obrázek musí být 16 pixelů a násobkem 16 pixelů na šířku.  
  
     Jednotlivé ikony je umístěn na rastrový obrázek vedle sebe v jediném řádku. Alfa kanál používá se k označení míst průhlednosti v jednotlivé ikony.  
  
     Pokud používáte 8bitové barevnou hloubku, použijte purpurová, `RGB(255,0,255)`, jako průhlednost. 32bitové barvy ikony jsou ale upřednostňované.  
  
2.  Zkopírujte soubor ikony *prostředky* adresáře ve vašem projektu VSPackage. V **Průzkumníka řešení**, přidejte ikonu do projektu. (Vyberte **prostředky**a v místní nabídce klepněte na příkaz **přidat**, pak **existující položku**a vyberte soubor ikony.)  
  
3.  Otevřít *.vsct* souboru v editoru.  
  
4.  Přidat `GuidSymbol` element s názvem **testIcon**. Vytvořit identifikátor GUID (**nástroje** > **Create GUID**a pak vyberte **formát registru** a klikněte na tlačítko **kopírování**) a vložte ho do `value` atribut. Výsledek by měl vypadat nějak takto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Přidat `<IDSymbol>` ikony. `name` Atribut je ID na ikonu a `value` označuje pozici na pruh, pokud existuje. Pokud existuje jenom jedna ikona, přidáte 1. Výsledek by měl vypadat nějak takto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Vytvoření `<Bitmap>` v `<Bitmaps>` část *.vsct* souboru k reprezentaci rastrový obrázek, který obsahuje ikony.  
  
    -   Nastavte `guid` hodnoty na název `<GuidSymbol>` elementu, kterou jste vytvořili v předchozím kroku.  
  
    -   Nastavte `href` hodnota, která má relativní cestu k souboru rastrového obrázku (v tomto případě **prostředky\\< název souboru ikony\>**.  
  
    -   Nastavte `usedList` hodnota, která má idsymbol – jste vytvořili dříve. Tento atribut Určuje čárkami oddělený seznam ikon pro použití v sady VSPackage. Jsou ikony není v seznamu vyloučených formuláře kompilace.  
  
         Blok rastrového obrázku by měl vypadat nějak takto:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  V existujícím `<Button>` element, nastaven `Icon` element na guidsymbol – a idsymbol – hodnoty, které jste vytvořili dříve. Tady je příklad prvku tlačítko s těmito hodnotami:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Testování vaší ikony. Sestavte projekt a spusťte ladění. V experimentální instanci najdete příkazu. Měl by se zobrazit ikonu, že jste přidali.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [Referenční dokumentace schématu VSCT XML](../extensibility/vsct-xml-schema-reference.md)
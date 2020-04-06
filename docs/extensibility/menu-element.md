---
title: Prvek nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702601"
---
# <a name="menu-element"></a>Prvek nabídky
Definuje jednu položku nabídky. Jedná se o šest druhů nabídek: Kontext, Menu, MenuController, MenuControllerLatched, Toolbar a ToolWindowToolbar.

## <a name="syntax"></a>Syntaxe

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje relativní polohu nabídky ve skupině nabídek.|
|ToolbarPriorityInBand|Nepovinný parametr. Číselná hodnota, která určuje relativní polohu panelu nástrojů v pásmu, když je okno ukotveno.|
|type|Nepovinný parametr. Výčet hodnota, která určuje druh prvku.<br /><br /> Pokud není k dispozici, výchozí typ je Menu.<br /><br /> Kontext<br /> Místní nabídka, která se zobrazí, když uživatel klepne pravým tlačítkem myši na okno. Místní nabídka má následující charakteristiky:<br /><br /> - Nepoužije pole **Nadřazený** a **Priorita,** pokud má být nabídka zobrazena jako místní nabídka.<br />- Může být použit jako podnabídka a také jako místní menu. V tomto případě jsou respektována pole **ID skupiny** i **priority.**<br />- Není vždy k dispozici.<br /><br /> Místní nabídka se zobrazí pouze v případě, že jsou splněny následující podmínky:<br /><br /> - Zobrazí se okno, které jej hostuje.<br />- Obslužná rutina myši v balíčku VSPackage detekuje klepnutí pravým tlačítkem myši na okno a pak zavolá metodu, která zpracovává příkaz.<br />- Místní nabídka se zobrazí <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> voláním metody (doporučený <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> přístup) nebo metody.<br /><br /> Nabídka<br /> Obsahuje rozevírací nabídku. Rozevírací nabídka má následující charakteristiky:<br /><br /> - Respektuje Parent ve své definici.<br />- Musí mít nadřazenou skupinu nebo CommandPlacement do skupiny.<br />- Může být podnabídka v jakémkoli jiném druhu menu.<br />- Automaticky se zobrazí vždy, když se zobrazí jeho nadřazené menu.<br />- Nevyžaduje implementaci žádného kódu VSPackage, aby byl zobrazen.<br /><br /> Kontrolka nabídky<br /> Obsahuje rozevírací nabídku rozděleného tlačítka, která se obvykle používá v panelech nástrojů. Nabídka MenuController má následující charakteristiky:<br /><br /> - Musí být obsažena v jiné nabídce prostřednictvím Parent nebo CommandPlacement.<br />- Respektuje Parent ve své definici.<br />- Může mít jakékoliv menu jako jeho rodič.<br />- Je automaticky k dispozici vždy, když je zobrazena nadřazená nabídka.<br />- Nevyžaduje programovou podporu, aby se nabídka zobrazí.<br /><br /> Na tlačítku nabídky se zobrazí příkaz z nabídky rozděleného tlačítka. Zobrazený příkaz má jednu z následujících vlastností:<br /><br /> - Jedná se o poslední příkaz, který byl použit, pokud je příkaz stále zobrazen a povolen.<br />- Jedná se o první zobrazený příkaz.<br /><br /> MenuControllerLatched<br /> Obsahuje rozevírací nabídku rozděleného tlačítka, pro kterou lze příkaz zadat jako výchozí výběr označením příkazu jako zámku.<br /><br /> Příkaz se zámkem je příkaz, který je v nabídce označen jako vybraný, obvykle zobrazením zaškrtnutí. Příkaz může být označen jako západka, pokud má OLECMDF_LATCHED příznak `QueryStatus` nastavit na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> něm v implementaci metody rozhraní. Nabídka MenuControllerLatched má následující charakteristiky:<br /><br /> - Musí být obsaženy v jiné nabídce prostřednictvím nadřazené skupiny nebo CommandPlacement.<br />- Respektuje Parent ve své definici.<br />- Může mít jakékoliv menu jako jeho rodič.<br />- Je k dispozici vždy, když je zobrazena nadřazená nabídka.<br />- Nevyžaduje programovou podporu, aby se nabídka zobrazí.<br /><br /> Na tlačítku nabídky se zobrazí příkaz z nabídky rozděleného tlačítka. Zobrazený příkaz má jednu z následujících vlastností:<br /><br /> - Jedná se o první zobrazený příkaz, který je zajištěn.<br />- Jedná se o první zobrazený příkaz.<br /><br /> Panel nástrojů<br /> Poskytuje panel nástrojů. Panel nástrojů má následující charakteristiky:<br /><br /> - Ignoruje Parent v jeho definici.<br />- Nelze vytvořit podnabídku žádné skupiny, a to ani pomocí CommandPlacement.<br />- Lze zobrazit vždy kliknutím na **panely nástrojů** v nabídce **Zobrazení.**<br />- Lze zobrazit pomocí [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- Nevyžaduje žádný kód k jeho vytvoření. Příklad vytvoření panelu nástrojů naleznete v [tématu Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Poskytuje panel nástrojů, který je připojen k určitému oknu nástroje, stejně jako panel nástrojů je připojen k vývojovému prostředí.<br /><br /> - Ignoruje Parent v jeho definici.<br />- Nelze vytvořit podnabídku žádné skupiny, a to ani pomocí CommandPlacement.<br />- Zobrazí se pouze v případě, že se zobrazí okno nástroje, které je hostitelem panelu nástrojů, a vspackage explicitně přidá panel nástrojů do okna nástroje. To se obvykle provádí při vytvoření okna nástroje získáním vlastnosti hostitele <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> panelu nástrojů (reprezentované rozhraním) z rámce okna nástroje a následným voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený prvek položky nabídky.|
|Příkaz Ový příznak|Povinná hodnota. Viz [Element command flag](../extensibility/command-flag-element.md). Platné hodnoty CommandFlag pro nabídku jsou následující:<br /><br /> -   **Alwayscreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** - Tento příznak nemá vliv na zobrazení panelů nástrojů.<br />-   **DontCache**<br />-   **DynamicVisibility** - Tento příznak nemá vliv na zobrazení panelů nástrojů.<br />-   **IconAndText**<br />-   **BezPřizpůsobení**<br />-   **NotInTBList**<br />-   **Zavřít panel NoToolbar**<br />-   **TextZměny**<br />-   **TextIsAnchorCommand**|
|Řetězce|Povinná hodnota. Viz [Strings element](../extensibility/strings-element.md). Podřízený `ButtonText` prvek musí být definován.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek nabídek](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|

## <a name="example"></a>Příklad

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>Viz také
- [Soubor příkazů Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

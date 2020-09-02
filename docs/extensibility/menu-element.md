---
title: Element nabídky | Microsoft Docs
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
ms.openlocfilehash: 020098a3026f600629b8ab186431a1d2d5d7795a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453658"
---
# <a name="menu-element"></a>Element menu
Definuje jednu položku nabídky. Jedná se o šest druhů nabídek: kontext, nabídka, MenuController, MenuControllerLatched, panel nástrojů a ToolWindowToolbar.

## <a name="syntax"></a>Syntax

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|
|upřednostněn|Nepovinný parametr. Číselná hodnota, která určuje relativní pozici nabídky ve skupině nabídek.|
|ToolbarPriorityInBand|Nepovinný parametr. Číselná hodnota, která určuje relativní pozici panelu nástrojů v pásmu, když je okno ukotveno.|
|typ|Nepovinný parametr. Výčtová hodnota, která určuje druh prvku.<br /><br /> Pokud není k dispozici, výchozí typ je nabídka.<br /><br /> Kontext<br /> Místní nabídka, která se zobrazí, když uživatel klikne pravým tlačítkem myši na okno. Místní nabídka má následující vlastnosti:<br /><br /> – Nepoužívá pole **nadřazený** a **Priorita** při zobrazení nabídky jako místní nabídky.<br />– Lze použít jako podnabídku a také jako místní nabídku. V tomto případě jsou respektovány obě pole **ID skupiny** i **Priorita** .<br />– Není vždy k dispozici.<br /><br /> Místní nabídka se zobrazí jenom v případě, že jsou splněné následující podmínky:<br /><br /> – Zobrazí se okno, které je hostované.<br />-Obslužná rutina myši ve VSPackage detekuje pravým kliknutím na okno a pak volá metodu, která zpracovává příkaz.<br />– Místní nabídka se zobrazí voláním <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> metody (doporučený postup) nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metody.<br /><br /> Nabídka<br /> Poskytuje rozevírací nabídku. Rozevírací nabídka má následující vlastnosti:<br /><br /> – Respektuje nadřazenou položku v její definici.<br />-Musí mít nadřazenou skupinu nebo CommandPlacement ke skupině.<br />– Může být podnabídka v jakémkoli jiném typu nabídky.<br />– Se automaticky zobrazí vždy, když se zobrazí jeho nadřazená nabídka.<br />– Nevyžaduje, aby se zobrazila žádná z kódů VSPackage.<br /><br /> MenuController<br /> Poskytuje rozevírací nabídku s rozděleným tlačítkem, která se obvykle používá na panelech nástrojů. MenuController nabídka má následující vlastnosti:<br /><br /> -Musí být obsažena v jiné nabídce nadřazené nebo CommandPlacement.<br />– Respektuje nadřazenou položku v její definici.<br />– Může mít libovolný druh nabídky jako svůj nadřazený objekt.<br />– Je automaticky k dispozici, kdykoli se zobrazí jeho nadřazená nabídka.<br />– Nevyžaduje programovou podporu pro zobrazení nabídky.<br /><br /> Příkaz z nabídky s rozděleným tlačítkem se zobrazí na tlačítku nabídky. Zobrazený příkaz má jednu z následujících vlastností:<br /><br /> – Jedná se o poslední příkaz, který byl použit, pokud je příkaz stále zobrazen a povolen.<br />– Jedná se o první zobrazený příkaz.<br /><br /> MenuControllerLatched<br /> Poskytuje rozevírací nabídku s rozdělenými tlačítky, pro kterou lze zadat příkaz jako výchozí výběr tak, že označíte příkaz jako západku.<br /><br /> Příkaz s západkou je příkaz, který je označený v nabídce jako vybraný, obvykle zobrazením značky zaškrtnutí. Příkaz může být označen jako západ, pokud má nastaven příznak OLECMDF_LATCHED v implementaci `QueryStatus` metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. MenuControllerLatched nabídka má následující vlastnosti:<br /><br /> – Musí být obsažena v jiné nabídce prostřednictvím nadřazené skupiny nebo CommandPlacement.<br />– Respektuje nadřazenou položku v její definici.<br />– Může mít libovolný druh nabídky jako svůj nadřazený objekt.<br />– Je k dispozici vždy, když se zobrazí jeho nadřazená nabídka.<br />– Nevyžaduje programovou podporu pro zobrazení nabídky.<br /><br /> Příkaz z nabídky s rozděleným tlačítkem se zobrazí na tlačítku nabídky. Zobrazený příkaz má jednu z následujících vlastností:<br /><br /> – Jedná se o první zobrazený příkaz, který je v západce.<br />– Jedná se o první zobrazený příkaz.<br /><br /> Panel nástrojů<br /> Poskytuje panel nástrojů. Panel nástrojů má následující vlastnosti:<br /><br /> -Ignoruje nadřazenou položku v její definici.<br />-Nelze vytvořit podnabídku žádné skupiny, a to ani pomocí CommandPlacement.<br />– Lze vždy zobrazit kliknutím na **panely nástrojů** v nabídce **zobrazení** .<br />– Dá se zobrazit pomocí [VisibilityItem](../extensibility/visibilityitem-element.md).<br />– Nevyžaduje žádný kód k jeho vytvoření. Příklad vytvoření panelu nástrojů naleznete v tématu [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Poskytuje panel nástrojů, který je připojen k určitému oknu nástroje, stejně jako panel nástrojů je připojen ke vývojovému prostředí.<br /><br /> -Ignoruje nadřazenou položku v její definici.<br />-Nelze vytvořit podnabídku žádné skupiny, a to ani pomocí CommandPlacement.<br />– Zobrazí se pouze v případě, že se zobrazí okno nástroje, které je hostitelem panelu nástrojů, a VSPackage explicitně přidá panel nástrojů do okna nástroje. To se obvykle provádí při vytvoření okna nástroje získáním vlastnosti hostitele panelu nástrojů (reprezentované <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> rozhraním) z rámce okna nástroje a následným voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody.|
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený prvek položky nabídky|
|CommandFlag|Povinná hodnota. Viz [element příznak příkazu](../extensibility/command-flag-element.md). Platné hodnoty CommandFlag pro nabídku jsou následující:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** – tento příznak neovlivňuje zobrazení panelů nástrojů.<br />-   **DontCache**<br />-   **DynamicVisibility** – tento příznak neovlivňuje zobrazení panelů nástrojů.<br />-   **IconAndText**<br />-   **Upravit**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Řetězce|Povinná hodnota. Viz [řetězec element](../extensibility/strings-element.md). `ButtonText`Musí být definován podřízený element.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Menu – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|

## <a name="example"></a>Příklad

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

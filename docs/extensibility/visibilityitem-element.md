---
title: Element VisibilityItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698152"
---
# <a name="visibilityitem-element"></a>Element VisibilityItem
`VisibilityItem`Prvek určuje statickou viditelnost příkazů a panelů nástrojů. Každá položka identifikuje příkaz nebo nabídku a také kontext uživatelského rozhraní příkazu. Visual Studio detekuje příkazy, nabídky a panely nástrojů a jejich viditelnost, aniž by bylo nutné načítat sady VSPackage, které je definují. Rozhraní IDE používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodu k určení, zda je kontext uživatelského rozhraní příkazu aktivní.

 Po načtení sady VSPackage aplikace Visual Studio očekává, že je viditelnost příkazu určena rozhraním VSPackage, nikoli `VisibilityItem` . Chcete-li zjistit viditelnost příkazu, můžete implementovat buď <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obslužnou rutinu události, nebo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu, v závislosti na způsobu implementace příkazu.

 Příkaz nebo nabídka, která má `VisibilityItem` element, se zobrazí pouze v případě, že je přidružený kontext aktivní. Jeden nebo více příkazů, nabídek nebo panelů nástrojů můžete přidružit k jednomu nebo více kontextům uživatelského rozhraní, a to tak, že zahrnete položku pro každou kombinaci kontextu příkazů. Pokud je příkaz nebo nabídka přidružená k více kontextům uživatelského rozhraní příkazu, pak je příkaz nebo nabídka zobrazená, pokud je aktivní kterýkoli z přidružených kontextů uživatelského rozhraní příkazu.

 `VisibilityItem`Element se vztahuje pouze na příkazy, nabídky a panely nástrojů, nikoli na skupiny. Element, který nemá související `VisibilityItem` prvek, je viditelný, kdykoli je jeho nadřazená nabídka aktivní.

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|
|kontext|Povinná hodnota. Kontext uživatelského rozhraní, ve kterém je příkaz viditelný.|
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`Prvek určuje statickou viditelnost skupin příkazů a panelů nástrojů.|

## <a name="remarks"></a>Poznámky
 Standardní kontexty uživatelského rozhraní sady Visual Studio jsou definovány v souboru *instalační cesty sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h a také v <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> třídách a. Ve třídě je definována úplnější sada kontextů uživatelského rozhraní <xref:Microsoft.VisualStudio.VSConstants> .

## <a name="example"></a>Příklad

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

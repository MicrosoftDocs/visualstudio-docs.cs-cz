---
title: Prvek VisibilityItem | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698152"
---
# <a name="visibilityitem-element"></a>VisibilityItem element
Prvek `VisibilityItem` určuje statickou viditelnost příkazů a panelů nástrojů. Každá položka identifikuje příkaz nebo nabídku a také přidružený kontext ui příkazu. Visual Studio detekuje příkazy, nabídky a panely nástrojů a jejich viditelnost, bez načtení VSPackages, které je definují. IDE používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodu k určení, zda je aktivní kontext ui příkazu.

 Po načtení VSPackage Visual Studio očekává, že viditelnost příkazu bude určena `VisibilityItem`VSPackage spíše než . Chcete-li zjistit viditelnost příkazu, můžete <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> implementovat obslužnou rutinu události nebo metodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> v závislosti na tom, jak jste implementovali příkaz.

 Příkaz nebo nabídka, `VisibilityItem` která má prvek, se zobrazí pouze v případě, že je aktivní přidružený kontext. Jeden příkaz, nabídku nebo panel nástrojů můžete přidružit k jednomu nebo více kontextům příkazového ui zahrnutím položky pro každou kombinaci kontextu příkazu. Pokud je příkaz nebo nabídka přidružena k více kontextům příkazu, je příkaz nebo nabídka viditelná, když je aktivní některý z přidružených kontextů hlavního nastavení příkazu.

 Prvek `VisibilityItem` se vztahuje pouze na příkazy, nabídky a panely nástrojů, nikoli na skupiny. Prvek, který nemá související `VisibilityItem` prvek, je viditelný vždy, když je aktivní jeho nadřazená nabídka.

## <a name="syntax"></a>Syntaxe

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|kontext|Povinná hodnota. Kontext ui, ve kterém je příkaz viditelný.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádný

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[VisibilityConstraints prvek](../extensibility/visibilityconstraints-element.md)|Prvek `VisibilityConstraints` určuje statickou viditelnost skupin příkazů a panelů nástrojů.|

## <a name="remarks"></a>Poznámky
 Standardní kontexty ui sady Visual Studio jsou definovány v *instalační cestě sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h a také ve třídách <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> a. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Úplnější sada kontextů ui je <xref:Microsoft.VisualStudio.VSConstants> definována ve třídě.

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
- [VisibilityConstraints prvek](../extensibility/visibilityconstraints-element.md)
- [Visual Studio příkaz tabulky (. Vsct) Soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

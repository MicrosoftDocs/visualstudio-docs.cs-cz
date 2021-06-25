---
title: VisibilityItem – | Microsoft Docs
description: Element VisibilityItem určuje statickou viditelnost příkazů a panelů nástrojů. Položky identifikují příkaz nebo nabídku a související kontext uživatelského rozhraní příkazu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 025e05dd0346c7da0a70985aa579d1673f2ffcaa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905433"
---
# <a name="visibilityitem-element"></a>VisibilityItem – element
Element `VisibilityItem` určuje statickou viditelnost příkazů a panelů nástrojů. Každá položka identifikuje příkaz nebo nabídku a také přidružený kontext uživatelského rozhraní příkazů. Visual Studio detekuje příkazy, nabídky a panely nástrojů a jejich viditelnost, aniž by načítaly balíčky VSPackage, které je definují. Integrované vývojové prostředí (IDE) <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> používá metodu k určení, zda je kontext uživatelského rozhraní příkazu aktivní.

 Po načtení balíčku VSPackage Visual Studio, že viditelnost příkazů určí balíček VSPackage místo `VisibilityItem` . Pokud chcete zjistit viditelnost příkazu, můžete implementovat buď obslužnou rutinu události, nebo metodu v závislosti na způsobu implementace <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> příkazu.

 Příkaz nebo nabídka, která má `VisibilityItem` prvek, se zobrazí pouze v případě, že je přidružený kontext aktivní. Jeden příkaz, nabídku nebo panel nástrojů můžete přidružit k jednomu nebo více kontextům uživatelského rozhraní příkazu zahrnutím položky pro každou kombinaci kontextu příkazu. Pokud je příkaz nebo nabídka přidružená k více kontextům uživatelského rozhraní příkazů, je příkaz nebo nabídka viditelná, když je aktivní některý z přidružených kontextů uživatelského rozhraní příkazů.

 Element se vztahuje pouze na příkazy, nabídky a `VisibilityItem` panely nástrojů, ne na skupiny. Element, který nemá související prvek, `VisibilityItem` je viditelný vždy, když je aktivní jeho nadřazená nabídka.

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|kontext|Povinná hodnota. Kontext uživatelského rozhraní, ve kterém je příkaz viditelný.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádná

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)|Element `VisibilityConstraints` určuje statickou viditelnost skupin příkazů a panelů nástrojů.|

## <a name="remarks"></a>Poznámky
 Standardní kontexty uživatelského rozhraní Visual Studio jsou definovány v instalační cestě sady *Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h a také ve třídách a <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Úplnější sada kontextů uživatelského rozhraní je definována ve <xref:Microsoft.VisualStudio.VSConstants> třídě .

## <a name="example"></a>Příklad

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)
- [Visual Studio příkazové tabulky (. Vsct) Soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

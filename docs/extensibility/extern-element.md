---
title: Extern Element | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711489"
---
# <a name="extern-element"></a>Extern prvek
Extern element odkazuje na všechny externí hlavičky (*.h*) soubory sloučit se souborem *.vsct* v době kompilace. Soubory, které mají být sloučeny, musí být na cestě Zahrnout, která je dána kompilátoru VSCT nebo na kterou odkazuje [prvek Include](../extensibility/include-element.md). Soubory mohou být jiné *soubory .vsct* nebo c++ hlavičkové soubory.

 Definice v souborech hlaviček musí mít tvar "#define [Symbol] [Value]" Hodnota může být jiným symbolem, pokud je dříve definována. Definice mohou být použity v podmíněných příkazech příkazových položek. Všechny symboly, které nebyly skutečně použity, budou zahozeny.

 CommandTable Element Extern Element

## <a name="syntax"></a>Syntaxe

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Href|Povinná hodnota. Cesta k souboru záhlaví:<br /><br /> href="stdidcmd.h"|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Nepovinný parametr. Výchozí jazyk všech [ \<řetězců>](../extensibility/strings-element.md) prvků v tabulce příkazů:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Žádné.|Žádné.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy – to znamená položky nabídky, nabídky, panely nástrojů a pole se seznamem – které vspackage poskytuje ide.|

## <a name="example"></a>Příklad

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Jak VSPackages přidat prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)

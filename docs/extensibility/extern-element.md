---
title: Extern – | Microsoft Docs
description: Element Extern odkazuje na všechny soubory externí hlavičky (.h), které se mají sloučit se souborem .vsct v době kompilace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 502b93f18aacfed26d3ea440c017e6de5281a35d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900184"
---
# <a name="extern-element"></a>Extern – element
Element Extern odkazuje na všechny soubory externí hlavičky (*.h*), které se mají sloučit se *souborem .vsct* v době kompilace. Soubory, které se mají sloučit, musí být na cestě Include předáné kompilátoru VSCT nebo odkazované [elementem Include](../extensibility/include-element.md). Soubory mohou být jiné *soubory .vsct* nebo hlavičkové soubory jazyka C++.

 Definice v souborech hlaviček musí mít tvar "#define [symbol] [hodnota]", hodnota může být dalším symbolem, pokud je definována dříve. Definice lze použít v podmíněných příkazových příkazových položkách. Jakýkoli symbol, který se ve skutečnosti nepouží, se zahodí.

 CommandTable Element Extern Element

## <a name="syntax"></a>Syntax

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Href|Povinná hodnota. Cesta k souboru hlaviček:<br /><br /> href="stdidcmd.h"|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Nepovinný parametr. Výchozí jazyk všech [\<Strings>](../extensibility/strings-element.md) prvků v tabulce příkazů:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Žádné|Žádné|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy – to znamená položky nabídky, nabídky, panely nástrojů a pole se seznamem – které balíček VSPackage poskytuje integrovanému vývojovému prostředí (IDE).|

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
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Jak balíčky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)

---
title: Zahrnout prvek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ea89185d28be2816a690d867dbb3eccbb739e04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710361"
---
# <a name="include-element"></a>Zahrnout prvek
Prvek Include určuje soubor, který může být umístěn na dodané cestě k vložení do aktuálního souboru.  Všechny definované symboly a typy se stanou součástí zkompilovaného výsledku.

## <a name="syntax"></a>Syntaxe

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Href|Povinná hodnota. Cesta k souboru záhlaví:<br /><br /> href="stdidcmd.h"|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Žádné.|Žádné.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy – to znamená položky nabídky, nabídky, panely nástrojů a pole se seznamem – které vspackage poskytuje ide.|

## <a name="example"></a>Příklad

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

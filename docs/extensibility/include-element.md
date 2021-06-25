---
title: Zahrnout element | Microsoft Docs
description: Element include určuje soubor, který může být umístěn v zadané cestě include pro vložení do aktuálního souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0005626c7fbb276775661a7cfb73d17f5e20d62
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899352"
---
# <a name="include-element"></a>Include – element
Element include určuje soubor, který může být umístěn v zadané cestě include pro vložení do aktuálního souboru.  Všechny symboly a typy, které jsou definovány, se stanou součástí zkompilovaného výsledku.

## <a name="syntax"></a>Syntax

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|odkaz|Povinná hodnota. Cesta k souboru hlaviček:<br /><br /> href = "Stdidcmd. h"|
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Žádné|Žádné|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element v příkazu](../extensibility/commandtable-element.md)|Definuje všechny prvky, které reprezentují příkazy, tj. položky nabídky, nabídky, panely nástrojů a pole se seznamem – to, že rozhraní VSPackage poskytuje integrované vývojové prostředí (IDE).|

## <a name="example"></a>Příklad

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

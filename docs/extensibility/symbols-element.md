---
title: Symbols – | Microsoft Docs
description: Element Symbols definuje identifikátory GUID a ID, které jsou používány jinými prvky VSCT. Tento článek obsahuje příklad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b593f353714f2fbb6f5b726fa2bbc0da449043ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901731"
---
# <a name="symbols-element"></a>Symbols – element
Definuje identifikátory GUID a ID používané jinými prvky VSCT. U nespravovaného kódu tyto informace obvykle pochází ze souborů hlaviček, které jsou určeny [externím elementem](../extensibility/extern-element.md). Spravovaný kód používá podřízené prvky elementu Symbols k definování těchto informací.

 Pokud vytvoříte soubor .vsct z existujícího souboru .cto, symboly se vygenerují jako podřízený prvek elementu Symbols. Další informace najdete v [tématu Postupy: Vytvoření . Soubor Vsct z existujícího souboru . Soubor Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Element Symbols by neměl být zaměňován s elementem [Define,](../extensibility/define-element.md)který definuje dvojice název-hodnota pro použití preprocesorem.

## <a name="syntax"></a>Syntax

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Description|
|---------------|-----------------|
|Žádná||

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|GuidSymbol|Definuje symbol GUID. GuidSymbol má dva povinné atributy: name a value. Název je název symbolu a hodnota je hodnota identifikátoru GUID jako řetězec.<br /><br /> Příklad:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definuje symbol. IDSymbol má dva povinné atributy: name a value. Název je název symbolu a hodnota je hodnota symbolu jako řetězec.<br /><br /> Příklad:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Kořenový element souboru .vsct.|

## <a name="example"></a>Příklad

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

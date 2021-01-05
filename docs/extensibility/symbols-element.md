---
title: Symbol – element | Microsoft Docs
description: Element Symbols definuje identifikátory GUID a ID, které používají jiné elementy VSCT. Tento článek obsahuje příklad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e86406c4c10c2f65e8e43d8f3cb67f413ed3c63
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715558"
---
# <a name="symbols-element"></a>Symbols – element
Definuje identifikátory GUID a ID, které používají jiné elementy VSCT. Pro nespravovaný kód tyto informace obvykle pocházejí ze hlavičkových souborů, které jsou určeny [extern element](../extensibility/extern-element.md). Spravovaný kód používá podřízené prvky elementu Symbols k definování těchto informací.

 Vytvoříte-li soubor. vsct z existujícího souboru. technický ředitel, symboly budou vygenerovány jako podřízené prvky elementu Symbols. Další informace naleznete v tématu [How to: Create a. Soubor vsct ze stávajícího souboru. Soubor technický ředitel](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

 Element Symbols by neměl být zaměněn pomocí [elementu define](../extensibility/define-element.md), který definuje páry název-hodnota pro použití preprocesorem.

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

|Atribut|Popis|
|---------------|-----------------|
|Žádná||

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|GuidSymbol|Definuje symbol identifikátoru GUID. GuidSymbol má dva povinné atributy: název a hodnota. Název je název symbolu a hodnota je hodnota identifikátoru GUID jako řetězec.<br /><br /> Například:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definuje symbol. IDSymbol má dva povinné atributy: název a hodnota. Název je název symbolu a hodnota je hodnota symbolu jako řetězec.<br /><br /> Například:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Kořenový element souboru. vsct.|

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

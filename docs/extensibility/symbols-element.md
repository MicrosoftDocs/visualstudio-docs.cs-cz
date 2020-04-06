---
title: Symboly Element | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699352"
---
# <a name="symbols-element"></a>Symbols – element
Definuje identifikátory GUID a ID, které jsou používány jinými prvky VSCT. U nespravovaného kódu tyto informace obvykle pocházejí ze souborů hlaviček, které jsou určeny [extern elementem](../extensibility/extern-element.md). Spravovaný kód používá k definování těchto informací podřízené prvky prvku Symbols.

 Pokud vytvoříte soubor .vsct z existujícího souboru .cto, symboly budou generovány jako podřízené prvky Symbols. Další informace naleznete v [tématu How to: Create a . Vsct soubor z existující . Cto soubor](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Symbols Element by neměl být zaměňován s [Define Element](../extensibility/define-element.md), který definuje dvojice název-hodnota pro použití preprocesorem.

## <a name="syntax"></a>Syntaxe

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
|Žádný||

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|Symbol guid|Definuje symbol GUID. GuidSymbol má dva požadované atributy: název a hodnotu. Název je název symbolu a hodnota je hodnota IDENTIFIKÁTORU GUID jako řetězce.<br /><br /> Například:\<GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|Symbol ID|Definuje symbol. IDSymbol má dva požadované atributy: název a hodnotu. Název je název symbolu a hodnota je hodnota symbolu jako řetězec.<br /><br /> Příklad:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Kořenový prvek souboru .vsct.|

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

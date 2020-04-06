---
title: Element commandtable | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739644"
---
# <a name="commandtable-element"></a>Element CommandTable
CommandTable je kořenový prvek souboru *.vsct.* Toto je soubor, který definuje skutečné rozložení a typ příkazů, které VSPackage poskytuje ide. Příkazy mohou obsahovat položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace naleznete v tématu [Visual Studio příkaz tabulka (.vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntaxe

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|-----------| - |
| Xmlns | Povinná hodnota. Obory názvů XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | Nepovinný parametr. Atribut jazyka lze použít k určení výchozího jazyka všech \<prvků Strings> v příkazové tabulce.  Pokud jazyk není zadán, bude použit jazyk aktuálního procesu:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Extern prvek](../extensibility/extern-element.md)|Nepovinný parametr. Obsahuje direktivy preprocesoru pro kompilátor.|
|[Zahrnout prvek](../extensibility/include-element.md)|Nepovinný parametr. Obsahuje cesty k libovolným souborům, které mají být zahrnuty do kompilace.|
|[Definovat prvek](../extensibility/define-element.md)|Nepovinný parametr. Definuje symbol s názvem a hodnotou.|
|[Element příkazy](../extensibility/commands-element.md)|Nepovinný parametr. Nadřazený prvek definující všechny příkazy pro VSPackage, který obsahuje všechny ostatní prvky.|
|[Element CommandPlacements](../extensibility/commandplacements-element.md)|Nepovinný parametr. Definuje, kam mají být na panelu příkazů umístěny.|
|[VisibilityConstraints prvek](../extensibility/visibilityconstraints-element.md)|Nepovinný parametr. Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[Element KeyBindings](../extensibility/keybindings-element.md)|Nepovinný parametr. Určuje případné kombinace klávesových zkratek pro příkazy.|
|[Element UsedCommands](../extensibility/usedcommands-element.md)|Nepovinný parametr. Umožňuje VSPackage volitelně implementovat vlastní verzi funkcí původně podporovaných jinými Balíčky VSPackages.|
|[Prvek symbolů](https://www.microsoft.com/download/details.aspx?id=55984)|Nepovinný parametr. Obsahuje všechna data symbolů -- GUID, ID a tak dále -- pro kompilátor.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|Žádný||

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

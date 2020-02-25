---
title: Element příkazu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f577b52ad2a9b1fd66ed9c24fb2737621aa8554c
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557778"
---
# <a name="commandtable-element"></a>Element v příkazu
Příkaz je kořenovým prvkem souboru *. vsct* . Jedná se o soubor, který definuje skutečné rozložení a typ příkazů, které rozhraní VSPackage poskytuje rozhraní IDE. Příkazy mohou zahrnovat položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace naleznete v tématu [soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|-----------| - |
| xmlns | Povinná hodnota. Obory názvů XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = "<http://www.w3.org/2001/XMLSchema>" |
| language | Volitelné. Atribut Language lze použít k určení výchozího jazyka všech \<řetězců > prvků v tabulce příkazů.  Pokud není zadán jazyk, bude použit jazyk aktuálního procesu:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[Extern – element](../extensibility/extern-element.md)|Volitelné. Obsahuje direktivy preprocesoru pro kompilátor.|
|[Include – element](../extensibility/include-element.md)|Volitelné. Obsahuje cesty k jakýmkoli souborům, které mají být zahrnuty do kompilace.|
|[Definovat element](../extensibility/define-element.md)|Volitelné. Definuje symbol zadaný jako název a hodnotu.|
|[Command – element](../extensibility/commands-element.md)|Volitelné. Nadřazený element definující všechny příkazy pro VSPackage, který obsahuje všechny ostatní prvky.|
|[Element CommandPlacements](../extensibility/commandplacements-element.md)|Volitelné. Určuje, kam se mají na panelu příkazů umístit příkazy.|
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Volitelné. Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[Element Bindings elementu](../extensibility/keybindings-element.md)|Volitelné. Určuje kombinace klávesových zkratek (pokud existují) pro příkazy.|
|[Element UsedCommands](../extensibility/usedcommands-element.md)|Volitelné. Umožňuje VSPackage volitelně implementovat svou vlastní verzi funkcí, které původně podporovaly jiné sady VSPackage.|
|[SYMBOLS – element](https://www.microsoft.com/download/details.aspx?id=55984)|Volitelné. Obsahuje jakákoli data symbolů – identifikátory GUID, ID a tak dále – pro kompilátor.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|Žádná||

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
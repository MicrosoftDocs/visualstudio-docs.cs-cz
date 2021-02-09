---
title: Element příkazu | Microsoft Docs
description: Příkaz je kořenovým prvkem souboru. vsct, který definuje rozložení a typ příkazů, které rozhraní VSPackage poskytuje rozhraní IDE.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79441880091088cf1d953c8925273e801dc0860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887351"
---
# <a name="commandtable-element"></a>Element v příkazu
Příkaz je kořenovým prvkem souboru *. vsct* . Jedná se o soubor, který definuje skutečné rozložení a typ příkazů, které rozhraní VSPackage poskytuje rozhraní IDE. Příkazy mohou zahrnovat položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace naleznete v tématu [soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntax

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
| xmlns | Povinná hodnota. Obory názvů XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| language | Nepovinný parametr. Atribut Language lze použít k určení výchozího jazyka všech \<Strings> prvků v tabulce příkazů.  Pokud není zadán jazyk, bude použit jazyk aktuálního procesu:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Extern – element](../extensibility/extern-element.md)|Nepovinný parametr. Obsahuje direktivy preprocesoru pro kompilátor.|
|[Include – element](../extensibility/include-element.md)|Nepovinný parametr. Obsahuje cesty k jakýmkoli souborům, které mají být zahrnuty do kompilace.|
|[Definovat element](../extensibility/define-element.md)|Nepovinný parametr. Definuje symbol zadaný jako název a hodnotu.|
|[Command – element](../extensibility/commands-element.md)|Nepovinný parametr. Nadřazený element definující všechny příkazy pro VSPackage, který obsahuje všechny ostatní prvky.|
|[Element CommandPlacements](../extensibility/commandplacements-element.md)|Nepovinný parametr. Určuje, kam se mají na panelu příkazů umístit příkazy.|
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Nepovinný parametr. Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[Element Bindings elementu](../extensibility/keybindings-element.md)|Nepovinný parametr. Určuje kombinace klávesových zkratek (pokud existují) pro příkazy.|
|[Element UsedCommands](../extensibility/usedcommands-element.md)|Nepovinný parametr. Umožňuje VSPackage volitelně implementovat svou vlastní verzi funkcí, které původně podporovaly jiné sady VSPackage.|
|[SYMBOLS – element](https://www.microsoft.com/download/details.aspx?id=55984)|Nepovinný parametr. Obsahuje jakákoli data symbolů – identifikátory GUID, ID a tak dále – pro kompilátor.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Description|
|-------------|-----------------|
|Žádná||

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

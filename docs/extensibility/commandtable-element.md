---
title: CommandTable – | Microsoft Docs
description: CommandTable je kořenový prvek souboru .vsct, který definuje rozložení a typ příkazů, které balíček VSPackage poskytuje integrovanému vývojovému prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 55faf4ee8bdc7ec261508fd07f5a573e7a29560f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901848"
---
# <a name="commandtable-element"></a>CommandTable – element
CommandTable je kořenový prvek *souboru .vsct.* Toto je soubor, který definuje skutečné rozložení a typ příkazů, které balíček VSPackage poskytuje integrovanému vývojovému prostředí. Příkazy mohou zahrnovat položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace najdete v [Visual Studio tabulky příkazů (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| Xmlns | Povinná hodnota. Obory názvů XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs=" <http://www.w3.org/2001/XMLSchema> " " |
| language | Nepovinný parametr. Atribut jazyka lze použít k určení výchozího jazyka všech \<Strings> prvků v tabulce příkazů.  Pokud jazyk není zadaný, použije se jazyk aktuálního procesu:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Extern – element](../extensibility/extern-element.md)|Nepovinný parametr. Obsahuje direktivy preprocesoru pro kompilátor.|
|[Include – element](../extensibility/include-element.md)|Nepovinný parametr. Obsahuje cesty k libovolným souborům, které mají být zahrnuty v kompilaci.|
|[Define – element](../extensibility/define-element.md)|Nepovinný parametr. Definuje symbol s daným názvem a hodnotou.|
|[Commands – element](../extensibility/commands-element.md)|Nepovinný parametr. Nadřazený prvek definující všechny příkazy pro balíček VSPackage, který obsahuje všechny ostatní prvky.|
|[CommandPlacements – element](../extensibility/commandplacements-element.md)|Nepovinný parametr. Definuje, kam na panelu příkazů se mají příkazy umístit.|
|[VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)|Nepovinný parametr. Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[KeyBindings – element](../extensibility/keybindings-element.md)|Nepovinný parametr. Určuje kombinace klávesových zkratek (pokud jsou k dispozici) pro příkazy.|
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Nepovinný parametr. Umožňuje balíčky VSPackage volitelně implementovat vlastní verzi funkcí, které původně podporovaly jiné balíčky VSPackage.|
|[Symboly – element](https://www.microsoft.com/download/details.aspx?id=55984)|Nepovinný parametr. Obsahuje jakákoli data symbolů – identifikátory GUID, ID atd. – pro kompilátor.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Description|
|-------------|-----------------|
|Žádná||

## <a name="see-also"></a>Viz také
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

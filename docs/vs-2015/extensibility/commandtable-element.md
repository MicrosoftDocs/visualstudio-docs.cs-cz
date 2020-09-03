---
title: Element příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477052"
---
# <a name="commandtable-element"></a>CommandTable – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkaz je kořenovým prvkem souboru. vsct. Jedná se o soubor, který definuje skutečné rozložení a typ příkazů, které rozhraní VSPackage poskytuje rozhraní IDE. Příkazy mohou zahrnovat položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
  
| Atribut |                                                                                                                   Popis                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Povinná hodnota. Obory názvů XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | Nepovinný parametr. Atribut Language lze použít k určení výchozího jazyka všech \<Strings> prvků v tabulce příkazů.  Pokud není zadán jazyk, bude použit jazyk aktuálního procesu:<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Extern – element](../extensibility/extern-element.md)|Nepovinný parametr. Obsahuje direktivy preprocesoru pro kompilátor.|  
|[Include – element](../extensibility/include-element.md)|Nepovinný parametr. Obsahuje cesty k jakýmkoli souborům, které mají být zahrnuty do kompilace.|  
|[Define – element](../extensibility/define-element.md)|Nepovinný parametr. Definuje symbol zadaný jako název a hodnotu.|  
|[Commands – element](../extensibility/commands-element.md)|Nepovinný parametr. Nadřazený element definující všechny příkazy pro VSPackage, který obsahuje všechny ostatní prvky.|  
|[CommandPlacements – element](../extensibility/commandplacements-element.md)|Nepovinný parametr. Určuje, kam se mají na panelu příkazů umístit příkazy.|  
|[VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)|Nepovinný parametr. Určuje statickou viditelnost příkazů a panelů nástrojů.|  
|[KeyBindings – element](../extensibility/keybindings-element.md)|Nepovinný parametr. Určuje kombinace klávesových zkratek (pokud existují) pro příkazy.|  
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Nepovinný parametr. Umožňuje VSPackage volitelně implementovat svou vlastní verzi funkcí, které původně podporovaly jiné sady VSPackage.|  
|[Symbols – element](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Nepovinný parametr. Obsahuje jakákoli data symbolů – identifikátory GUID, ID a tak dále – pro kompilátor.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Žádné||  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

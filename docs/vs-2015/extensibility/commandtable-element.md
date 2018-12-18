---
title: Commandtable – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1adc3e8f8c7894cfb3a55617ce594f52a60f2498
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817370"
---
# <a name="commandtable-element"></a>CommandTable – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commandtable – je kořenovým prvkem souboru .vsct. Toto je soubor, který definuje skutečný rozložení a typ příkazů, které poskytuje VSPackage pro prostředí IDE. Příkazy mohou být položky nabídky, nabídky, panely nástrojů a pole se seznamem. Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|   atribut xmlns   |                                   Požadováno. Obory názvů XML:<br /><br /> atribut xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs = "<http://www.w3.org/2001/XMLSchema>"                                   |
| jazyk  | Volitelné. Atribut language slouží k určení výchozí jazyk všech \<řetězce > prvků v tabulce příkazu.  Pokud jazyk není zadán, použije se jazyk aktuálního procesu:<br /><br /> jazyk = "en-us" |
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Extern – element](../extensibility/extern-element.md)|Volitelné. Obsahuje direktivy preprocesoru kompilátoru jazyka.|  
|[Include – element](../extensibility/include-element.md)|Volitelné. Obsahuje cesty k souborům, které chcete zahrnout do kompilace.|  
|[Define – element](../extensibility/define-element.md)|Volitelné. Definuje symbol zadanou její název a hodnotu.|  
|[Commands – element](../extensibility/commands-element.md)|Volitelné. Definování všechny příkazy pro sady VSPackage, která obsahuje všechny ostatní prvky nadřazeného elementu.|  
|[CommandPlacements – element](../extensibility/commandplacements-element.md)|Volitelné. Definuje, kde na panelu příkazů příkazy mají být umístěny.|  
|[VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)|Volitelné. Určuje statické viditelnost příkazů a panely nástrojů.|  
|[KeyBindings – element](../extensibility/keybindings-element.md)|Volitelné. Určuje kombinace klávesových zkratek, pokud existuje, pro příkazy.|  
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Volitelné. Umožňuje VSPackage volitelně implementovat svou vlastní verzi funkce původně podporuje další rozšíření VSPackages.|  
|[Symbols – element](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Volitelné. Obsahuje všechna data symbol--identifikátory GUID, ID a tak dále--pro kompilátor.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Žádné||  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


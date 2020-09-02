---
title: Element VisibilityConstraints | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f6a74fabfc1bd86f54656c6b30b55690940a0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62585123"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element VisibilityConstraints určuje statickou viditelnost skupin příkazů a panelů nástrojů. Viditelnost je nejprve ovládána [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaným vývojovým prostředím (IDE) bez načtení balíčku VSPackage.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[VisibilityItem – element](../extensibility/visibilityitem-element.md)|Určuje statickou viditelnost příkazů a panelů nástrojů.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Určuje statickou viditelnost skupin příkazů a panelů nástrojů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy (například položky nabídky, nabídky, panely nástrojů a pole se seznamem), které rozhraní VSPackage poskytuje integrovanému vývojovému prostředí (IDE).|  
  
## <a name="example"></a>Příklad  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Viz také  
 [Element VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: Visibilityconstraints – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ade6f2ac15d5b1c46b9b388d13b52d87129a66b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930268"
---
# <a name="visibilityconstraints-element"></a>Visibilityconstraints – element
Visibilityconstraints – element určuje statické viditelnost skupiny příkazů a panely nástrojů. Nejprve řídí viditelnost [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) bez načtení sady VSPackage.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
|Podmínka|Volitelné. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Visibilityitem – element](../extensibility/visibilityitem-element.md)|Určuje statické viditelnost příkazů a panely nástrojů.|  
|[Visibilityconstraints –](../extensibility/visibilityconstraints-element.md)|Určuje, zda statických skupin příkazů a panely nástrojů.|  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Commandtable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy (například položek nabídky, nabídky, panely nástrojů a pole se seznamem), které poskytuje VSPackage pro prostředí IDE.|  
  
## <a name="example"></a>Příklad  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Visibilityitem – element](../extensibility/visibilityitem-element.md)   
 [Visual Studio tabulky příkazů (. Soubory Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
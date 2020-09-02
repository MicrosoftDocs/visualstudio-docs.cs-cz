---
title: Element UsedCommand | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186370"
---
# <a name="usedcommand-element"></a>UsedCommand – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umožňuje VSPackage získat přístup k příkazu, který je definován v jiném souboru. vsct. Pokud například vaše VSPackage používá příkaz standardního **kopírování** , který je definován [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředím, můžete příkaz Přidat do nabídky nebo panelu nástrojů, aniž byste ho znovu implementovali.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|guid|Povinná hodnota. Identifikátor GUID páru identifikátorů GUID, který identifikuje příkaz|  
|id|Povinná hodnota. ID páru identifikátorů GUID, který identifikuje příkaz|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Žádné||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Seskupí prvky UsedCommand a další skupiny UsedCommands.|  
  
## <a name="remarks"></a>Poznámky  
 Přidáním příkazu do `<UsedCommands>` prvku VSPackage informuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí, které VSPackage vyžaduje příkaz. Měli byste přidat `<UsedCommand>` element pro libovolný příkaz, který váš balíček vyžaduje, aby se nezahrnuly do všech verzí a konfigurací sady Visual Studio. Například pokud váš balíček volá příkaz, který je specifický pro Visual C++, nebude příkaz uživatelům aplikace Visual Web Developer k dispozici, Pokud nezahrnete `<UsedCommand>` prvek pro příkaz.  
  
## <a name="example"></a>Příklad  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Viz také  
 [Element UsedCommands](../extensibility/usedcommands-element.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

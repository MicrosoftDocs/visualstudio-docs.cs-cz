---
title: CustomParameter – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d5de5d2265cfa59285f92e3426fefce3d770933
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788612"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje název vlastní parametr a hodnotu použijte, pokud projekt nebo položku je vytvořen z šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Název parametru Formát pro parametry je $*název*$.|  
|`Value`|Požadováno. Nahrazující hodnotou parametru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[CustomParameters –](../extensibility/customparameters-element-visual-studio-templates.md)|Skupiny vlastní parametry, které mají být předány do Průvodce vytvořením šablony, když Průvodce provede nahrazení parametru.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud šablona obsahuje `CustomParameter` prvky, každá instance `Name` nahradí atribut `Value` atribut v vytvořené soubory projektu nebo položky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít několik vlastních parametrů v šabloně. Při vytvoření projektu nebo položky ze šablony s následující vlastní parametry všechny výskyty `$color1$` a `$color2$` v šabloně se nahradí soubory `Red` a `Blue`v uvedeném pořadí.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Viz také  
 [CustomParameters – Element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)


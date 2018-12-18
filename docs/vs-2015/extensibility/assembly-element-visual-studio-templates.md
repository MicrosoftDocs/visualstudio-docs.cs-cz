---
title: Assembly – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40bb0b99bfe22c7842296c2fbaa2b868ca1ef259
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802028"
---
# <a name="assembly-element-visual-studio-templates"></a>Element sestavení (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o sestavení, který používá šablonu přidáte odkaz na toto sestavení do projektů.  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<Odkazy >  
 \<Odkaz >  
 \<Sestavení >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Referenční informace](../extensibility/reference-element-visual-studio-templates.md)|Určuje odkaz na sestavení přidat, pokud je položka přidána do projektu.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Tento text určuje sestavení, které chcete přidat do projektu při vytváření instance šablony položky. Tento název sestavení musí být zadán v jednom z následujících způsobů:  
  
-   Jako název úplné sestavení. Příklad:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Jako jednoduchý text odkazu. Příklad:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Poznámky  
 `Assembly` je vyžadovaný podřízený prvek `Reference`.  
  
 `Reference`, `References,` a `Assembly` prvky lze použít pouze v souborech .vstemplate, které mají `Type` hodnotu atributu `Item`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, `TemplateContent` elementu šablony položky. Tato konfigurace XML přidá odkazy na sestavení System.dll a System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)


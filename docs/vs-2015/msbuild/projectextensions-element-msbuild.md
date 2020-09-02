---
title: ProjectExtensions – – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0afc4f73ed287f753acf87bd0b112e6f5303e996
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551248"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Povoluje, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aby soubory projektu obsahovaly neobsahující [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] informace. Cokoli uvnitř `ProjectExtensions` elementu bude ignorováno [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
 \<Project>  
 \<ProjectExtensions>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
  
## <a name="remarks"></a>Poznámky  
 `ProjectExtensions`V projektu lze použít pouze jeden prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje informace z integrovaného vývojového prostředí, které je uloženo v `ProjectExtensions` prvku.  
  
```  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [Nástroji](msbuild.md)

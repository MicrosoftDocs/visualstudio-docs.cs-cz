---
title: Úloha XmlPoke – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ba57c1578bd69d71ed0abdac45907d937b89ecb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198973"
---
# <a name="xmlpoke-task"></a>XmlPoke – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastaví hodnoty určené dotazem XPath do souboru XML.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `XmlPoke` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Namespaces`|Volitelný `String` parametr.<br /><br /> Určuje obory názvů pro předpony dotazů XPath.|  
|`Query`|Volitelný `String` parametr.<br /><br /> Určuje dotaz XPath.|  
|`Value`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje výstupní soubor.|  
|`XmlInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstup XML jako cestu k souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)

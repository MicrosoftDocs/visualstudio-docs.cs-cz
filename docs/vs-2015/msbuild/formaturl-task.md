---
title: Úloha FormatUrl – | Microsoft Docs
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
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb870bcc3c4297d5d1b403176f931f75e418d423
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149715"
---
# <a name="formaturl-task"></a>FormatUrl – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Převede adresu URL na správný formát adresy URL.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `FormatUrl` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`InputUrl`|Volitelný `String` parametr.<br /><br /> Určuje adresu URL, která má být naformátovaná.|  
|`OutputUrl`|Volitelný `String` výstupní parametr.<br /><br /> Určuje formátovanou adresu URL.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)

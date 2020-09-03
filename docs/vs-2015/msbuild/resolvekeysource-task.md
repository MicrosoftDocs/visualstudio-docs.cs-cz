---
title: Úloha ResolveKeySource – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5cbe2f4998ab78ce39cde4b26a38b13c70b2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193721"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje zdroj klíče se silným názvem.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `ResolveKeySource` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Volitelný `Int32` parametr.<br /><br /> Získá nebo nastaví množství času (v sekundách), ve kterém se má zobrazit zpráva o počtu.|  
|`AutoClosePasswordPromptTimeout`|Volitelný `Int32` parametr.<br /><br /> Získá nebo nastaví množství času (v sekundách), po který se má čekat před zavřením dialogového okna výzvy k zadání hesla.|  
|`CertificateFile`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví cestu k souboru certifikátu.|  
|`CertificateThumbprint`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví kryptografický otisk certifikátu.|  
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví cestu k souboru klíče.|  
|`ResolvedKeyContainer`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví vyřešený kontejner klíčů.|  
|`ResolvedKeyFile`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví přeložený soubor klíče.|  
|`ResolvedThumbprint`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví přeložený kryptografický otisk certifikátu.|  
|`ShowImportDialogDespitePreviousFailures`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se zobrazí dialogové okno pro import navzdory předchozím selháním.|  
|`SuppressAutoClosePasswordPrompt`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda se má dialogové okno výzvy k zadání hesla automaticky zavřít.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)

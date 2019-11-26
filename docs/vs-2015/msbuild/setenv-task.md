---
title: Úloha setenv – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc9b15efb8fca12382fae94912d22c39b96bd4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295976"
---
# <a name="setenv-task"></a>SetEnv – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastaví nebo odstraní hodnotu zadané proměnné prostředí.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **setenv –** .  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**Jméno**|Povinný parametr **řetězce**<br /><br /> Název proměnné prostředí.|  
|**OutputEnvironmentVariable**|Volitelný výstupní parametr **řetězce** .<br /><br /> Obsahuje hodnotu, která je přiřazena proměnné prostředí, která je určena parametrem **Name** .|  
|**Směr**|Povinný parametr `Boolean`.<br /><br /> Pokud `true`, zřetězí hodnotu parametru **Value** před hodnotu proměnné prostředí, která je určena parametrem **Name** , a poté přiřadí výsledek proměnné prostředí. Pokud `false`, přiřadí pouze hodnotu parametru **Value** proměnné prostředí.|  
|**Cílové**|Volitelný **řetězcový** parametr.<br /><br /> Určuje umístění, kde je uložena proměnná prostředí. Zadejte "`User`" nebo "`Machine`".<br /><br /> Další informace najdete v části "výčet EnvironmentVariableTarget" na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .|  
|**Hodnota**|Volitelný **řetězcový** parametr.<br /><br /> Hodnota přiřazená proměnné prostředí, která je určena parametrem **Name** Pokud je **hodnota** prázdná a proměnná existuje, proměnná se odstraní. Pokud proměnná neexistuje, nedošlo k žádné chybě, i když operaci nelze provést.<br /><br /> Další informace naleznete v části "prostředí:: SetEnvironmentVariable metoda" na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)

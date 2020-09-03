---
title: Osvědčené postupy nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181113"
---
# <a name="msbuild-best-practices"></a>Doporučené postupy nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro psaní skriptů MSBuild doporučujeme následující osvědčené postupy:  
  
- Výchozí hodnoty vlastností jsou nejlépe zpracovávány pomocí `Condition` atributu a nikoli deklarováním vlastnosti, jejíž výchozí hodnota může být přepsána v příkazovém řádku. Například použijte  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Vyhněte se zástupným znakům při výběru položek. Místo toho zadejte soubory explicitně. To usnadňuje sledování chyb, které mohou nastat při přidávání nebo odstraňování souborů.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)

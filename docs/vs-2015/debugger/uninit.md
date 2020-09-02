---
title: Neinicializovat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197937"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Poznámky  
 `UnInit` se nazývá automaticky `VsgDbg` , když je zničena instance třídy. Pokud `VsgDbg` instance aktivně nezaznamenává informace o grafice, nemá to žádný vliv.  
  
 Po zavolání `UnInit` na instanci `VsgDbg` třídy lze nový soubor protokolu grafiky vytvořit voláním `Init` a finalizován voláním `UnInit` . Tento postup můžete opakovat tolikrát, kolikrát chcete stejnou `VsgDbg` instanci použít k vytvoření několika nezávislých souborů protokolu grafiky.  
  
## <a name="see-also"></a>Viz také  
 [For](../debugger/init.md)

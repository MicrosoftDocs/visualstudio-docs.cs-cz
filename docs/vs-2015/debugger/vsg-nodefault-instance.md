---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c7d2263642c2ff8a2c36f274d2c7b80745ed845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179483"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje podle své přítomnosti, jestli je dodána výchozí instance třídy [VsgDbg třídy](../debugger/vsgdbg-class.md) , která poskytuje rozhraní pro programové zachycení.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Hodnota  
 Symbol preprocesoru, který podle jeho přítomnosti nebo absence určuje, zda `VsgDbg` je zadána výchozí instance třídy. Pokud je tento symbol definován, není `VsgDbg` k dispozici žádná výchozí instance třídy; v opačném případě je před spuštěním programu zadána a inicializována výchozí instance.  
  
 Programové rozhraní pro zachycení je k dispozici prostřednictvím ukazatele, který má globální rozsah `g_pVsgDbg` .  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Poznámky  
 Výchozí instance je často dostatečná, ale chcete-li použít rozhraní programového zachycení v knihovně DLL, když bylo zařízení D3D vytvořeno mimo tuto knihovnu DLL, je nutné vytvořit a spravovat vlastní instanci `VsgDbg` třídy. Pokud tímto způsobem spravujete vlastní rozhraní rozhraní API pro programové zachycení, zakažte výchozí instanci definováním `VSG_NODEFAULT_INSTANCE` tak, aby se předešlo režii.  
  
 Pokud výchozí instance není zakázána, je automaticky inicializována před spuštěním programu a bude automaticky zničena při ukončení programu. Nemusíte inicializovat nebo odinicializovat tuto instanci explicitně.  
  
 Chcete-li zakázat výchozí instanci, je nutné definovat `VSG_NODEFAULT_INSTANCE` před zahrnutím `vsgcapture.h` do programu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak zakázat výchozí instanci:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```

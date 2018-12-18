---
title: VSG_NODEFAULT_INSTANCE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43affa6db83d34d18a3f485a88f41ccde5d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804408"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje jeho přítomnost, zda výchozí instanci [třída VsgDbg](../debugger/vsgdbg-class.md) třídy – poskytující rozhraní zachytávání prostřednictvím kódu programu – pochází.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Hodnota  
 Preprocesoru symbol, který podle jeho přítomnost nebo absence Určuje, zda výchozí instanci `VsgDbg` třídy je k dispozici. Pokud tento symbol není definován, pak žádný výchozí instanci `VsgDbg` třídy je k dispozici; jinak je výchozí instance k dispozici a inicializován před spuštěním programu.  
  
 Programové zachytávání rozhraní je k dispozici prostřednictvím ukazatele, který má globální obor, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Poznámky  
 Výchozí instance je často dostatečné, ale pokud chcete použít rozhraní zachytávání prostřednictvím kódu programu uvnitř knihovny DLL, po vytvoření zařízení D3D mimo tuto knihovnu DLL, musíte vytvořit a spravovat vlastní instance `VsgDbg` třídy. Pokud spravujete vlastní rozhraní pro zachytávání prostřednictvím kódu programu API tímto způsobem, zakázat výchozí instanci definováním `VSG_NODEFAULT_INSTANCE` , aby režijní náklady.  
  
 Pokud není výchozí instancí zakázán, je automaticky inicializován před spuštěním vaší aplikace a automaticky je zničen při ukončení programu. Není nutné inicializovat nebo explicitně uninitialize této instance.  
  
 Chcete-li zakázat výchozí instanci, je nutné definovat `VSG_NODEFAULT_INSTANCE` teprve potom zahrňte `vsgcapture.h` ve svém programu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak zakázat výchozí instanci:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```




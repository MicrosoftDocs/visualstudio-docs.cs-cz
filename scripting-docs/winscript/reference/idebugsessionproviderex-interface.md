---
title: Idebugsessionproviderex – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794232"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx – rozhraní
Primární rozhraní služby IDE, pokud chcete povolit ladění spustil hostitele a jazyk ladicí program. Navazuje na relaci ladění pro běžící aplikaci. Toto rozhraní je implementováno modulem Machine Manager ladění.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugSessionProviderEx` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Určuje, zda pouze v době ladění je možné pomocí zadané aplikace.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Spustí relaci ladění pomocí zadané aplikace.|
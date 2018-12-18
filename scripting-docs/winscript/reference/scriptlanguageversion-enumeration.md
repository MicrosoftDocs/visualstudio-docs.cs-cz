---
title: SCRIPTLANGUAGEVERSION – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796374"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION – výčet
Určuje možné skriptování verze.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Výchozí verze. Celočíselná hodnota je 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows skriptování verzi 5.7. Celočíselná hodnota je 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Verze 5.8 skriptů systému Windows. Celočíselná hodnota je 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Maximální verze. Celočíselná hodnota je 255.|  
  
## <a name="see-also"></a>Viz také  
 [Aktivních skriptů konstanty, výčty a kódy chyb](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
---
title: 'Ienumdebugpropertyinfo –:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574158"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Přeskočí zadaný počet `DebugPropertyInfo` struktur v sekvenci výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet `DebugPropertyInfo` struktur v sekvenci výčtu k přeskočení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`. Vrátí `S_FALSE` a nastaví ukazatel na element Current elementu na konec výčtu, pokud je `celt` větší než počet prvků zbývajících v enumerátoru.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní ienumdebugpropertyinfo –](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [DebugPropertyInfo – struktura](../../winscript/reference/debugpropertyinfo-structure.md)
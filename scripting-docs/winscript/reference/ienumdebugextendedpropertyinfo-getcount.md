---
title: 'Ienumdebugextendedpropertyinfo –:: GetCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::GetCount
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b51e4cd765a03226800af95b5de318862d87946
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576839"
---
# <a name="ienumdebugextendedpropertyinfogetcount"></a>IEnumDebugExtendedPropertyInfo::GetCount
Získá počet `ExtendedDebugPropertyInfo` struktur v enumerátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 mimo Vrátí počet `ExtendedDebugPropertyInfo` struktur v enumerátoru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní ienumdebugextendedpropertyinfo –](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [ExtendedDebugPropertyInfo – struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
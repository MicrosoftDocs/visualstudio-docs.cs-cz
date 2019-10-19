---
title: 'Idebugproperty –:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562391"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Získá Rozšířené informace o vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cInfos`  
 pro Počet rozšířených informačních objektů  
  
 `rgguidExtendedInfo`  
 pro Pole `GUID`s je předáno, aby bylo možné načíst více položek rozšířených informací současně.  
  
 `pExtendedInfo`  
 mimo Vrátí pole `VARIANT`s, které lze použít k načtení informací rozšířených vlastností.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní získá rozšířené informace pro tento objekt. Rozhraní API existuje pouze pro účely načítání informací, které neslouží k načtení pomocí `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Viz také:  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)
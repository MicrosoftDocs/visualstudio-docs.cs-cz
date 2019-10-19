---
title: 'Iscriptentry –:: SetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575338"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Nastaví informace o typu `IScriptEntry` objektu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pti`  
 pro Informace o typu.  
  
 `iMethod`  
 pro Index metody v objektu `ITypeInfo`.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Informace o typu se nastavují pomocí `IScriptEntry::SetSignature` nebo [iscriptnode –:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informace o typu mohou být vygenerovány také položkou na základě reprezentace vnitřní funkce.  
  
## <a name="see-also"></a>Viz také:  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)
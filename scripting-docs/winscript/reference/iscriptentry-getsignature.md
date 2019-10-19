---
title: 'Iscriptentry –:: getsignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575423"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Vrátí informace o typu objektu `IScriptEntry` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppti`  
 mimo Informace o typu přidružené k tomuto `IScriptEntry`mu objektu funkce.  
  
 `piMethod`  
 mimo Index metody v objektu `ITypeInfo`.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Informace o typu se nastavují pomocí [iscriptentry –:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) nebo [Iscriptnode –:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informace o typu mohou být vygenerovány také položkou na základě reprezentace vnitřní funkce.  
  
## <a name="see-also"></a>Viz také:  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)
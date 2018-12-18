---
title: ICanHandleException::CanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793728"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Určuje, pokud má volající skriptovací stroj může zpracovat zadanou výjimkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcepInfo`  
 [v] Ukazatel na `EXCEPINFO` struktura obsahující informace, která bude hlášena, pokud je nalezena žádná obslužná rutina výjimky.  
  
 `pvar`  
 [v] Hodnotu související s tím rozdílem, jako je například hodnota vyvolané `throw` příkaz. Tento parametr může být `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volající může zpracovat výjimku|  
|`E_FAIL`|Volající nemůže být zpracována výjimka.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud volání `IDispatchEx::InvokeEx`, nebo podobné metody, má za následek výjimku kontroly modul skriptu pro volající v řetězu volající ke skriptu, který podporuje `ICanHandleException` rozhraní a určuje, že může zpracovat výjimku. Pokud žádné volající může zpracovat výjimku, skriptovací stroj se zastaví.  
  
## <a name="see-also"></a>Viz také  
 [Icanhandleexception – rozhraní](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)
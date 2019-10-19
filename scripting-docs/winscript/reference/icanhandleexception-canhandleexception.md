---
title: 'Icanhandleexception –:: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575712"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Určuje, zda volající skriptovací modul může zpracovat určenou výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcepInfo`  
 pro Ukazatel na strukturu `EXCEPINFO` obsahující informace, které budou hlášeny, pokud nebyla nalezena žádná obslužná rutina výjimky.  
  
 `pvar`  
 pro Hodnota spojená s výjimkou, jako je například hodnota vyvolaná příkazem `throw`. Tento parametr může být `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volající může zpracovat výjimku.|  
|`E_FAIL`|Volající nemůže zpracovat výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud volání `IDispatchEx::InvokeEx`, nebo podobná metoda, má za následek výjimku, skriptovací modul kontroluje volající v řetězu volajícího skriptu, který podporuje rozhraní `ICanHandleException` a označuje, že může zpracovat výjimku. Pokud žádný volající nedokáže zpracovat výjimku, skriptovací stroj se zastaví.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní icanhandleexception –](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)
---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573011"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato metoda načte hodnotu zadané místní proměnné jako nezpracované bajty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInstance`  
 pro `IDiaLVarInstance` Objekt představující instanci lokální proměnné pro získání hodnoty pro.  
  
 `cbDataMax`  
 pro Maximální počet bajtů ve vyrovnávací paměti, na které ukazuje `pbData` . Může to být maximálně 8 bajtů ( `sizeof(ULONGLONG)` ).  
  
 `pcbData`  
 mimo Vrátí skutečný počet bajtů uložených ve vyrovnávací paměti.  
  
 `pbData`  
 mimo Vyrovnávací paměť, která se má vyplnit daty. To nemůže být `NULL` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

---
title: IActiveScriptError::GetExceptionInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8719d1a169c89d7b6cf712a125b6962b9c7a8839
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793308"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Načte informace o chybu, ke které došlo k chybě skriptování modul byl spuštěn skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pexcepinfo`  
 [out] Adresa `EXCEPINFO` struktura, která přijímá informace o chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_FAIL` Pokud došlo k chybě.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescripterror –](../../winscript/reference/iactivescripterror.md)
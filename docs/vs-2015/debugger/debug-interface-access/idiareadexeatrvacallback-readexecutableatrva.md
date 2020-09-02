---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187265"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte zadaný počet bajtů počínaje zadanou relativní virtuální adresou (RVA) ze spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `relativeVirtualAddress`  
 pro Adresa RVA ve spustitelném souboru pro zahájení čtení.  
  
 `cbData`  
 pro Počet bajtů, které se mají přečíst  
  
 `pcbData`  
 mimo Vrátí počet přečtených bajtů.  
  
 `data[]`  
 [in, out] Pole, které je vyplněno bajty přečtenými ze souboru.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána kódem podpory DIA k načtení datových bajtů ze spustitelného souboru pomocí relativní virtuální adresy. Tato metoda je volána v podpoře metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

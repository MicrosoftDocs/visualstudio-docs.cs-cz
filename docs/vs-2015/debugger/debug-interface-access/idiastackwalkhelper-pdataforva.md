---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150092"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vrátí blok dat PDATA přidružený k virtuální adrese.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 pro Určuje virtuální adresu dat, která se mají získat.  
  
 `cbData`  
 pro Velikost dat v bajtech, která se má získat  
  
 `pcbData`  
 mimo Vrátí skutečnou velikost dat v bajtech, které byly získány.  
  
 `pbData`  
 [in, out] Vyrovnávací paměť, která je vyplněna požadovanými daty. Nemůže být `NULL` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud pro zadanou adresu není k dispozici žádný PDATA. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 PDATA (oddíl s názvem ". pdata") kompilantu obsahuje informace o zpracování výjimek pro funkce.  
  
 Volající ví, kolik dat se má vrátit, aby volající nemusel klást informace o tom, kolik dat je k dispozici. Proto je přijatelné k tomu, aby implementace této metody vrátila chybu, pokud `pbData` je parametr `NULL` .  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

---
title: IDiaStackWalkHelper::pdataForVA | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c937ac3039ef5807623d99a9d7fcaadada17a3e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816746"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vrátí přidružený virtuální adresu PDATA datového bloku.  
  
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
 [in] Určuje virtuální adresu dat, která poskytuje.  
  
 `cbData`  
 [in] Velikost dat v bajtech získat.  
  
 `pcbData`  
 [out] Vrátí skutečný objem dat v bajtech, ke které byl získán.  
  
 `pbData`  
 [out v] Vyrovnávací paměť je vyplní požadovaná data. Nemůže být `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` Pokud neexistuje žádný PDATA pro zadanou adresu. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 PDATA (oddíl s názvem ".pdata") kompilace obsahuje informace o zpracování výjimek pro funkce.  
  
 Volající ví, kolik dat má být vrácen tak má volající není potřeba zeptejte, kolik dat je k dispozici. Proto je přijatelné pro implementace této metody vrátit chybu, pokud `pbData` parametr `NULL`.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)




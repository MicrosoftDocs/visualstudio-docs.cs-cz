---
title: Idiaenumsymbolsbyaddr::symbolbyva – | Dokumentace Microsoftu
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
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b383b0ad61f3bf9042b4ccaa794301c948718ad2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777505"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pozice výčtu pomocí provádí vyhledávání podle virtuální adresy (VA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 virtualAddress  
 [in] Virtuální adresa.  
  
 ppsymbol  
 [out] Vrátí [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objekt představující symbol nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` Pokud symbol se nenašel. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Idiaenumsymbolsbyaddr –](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)




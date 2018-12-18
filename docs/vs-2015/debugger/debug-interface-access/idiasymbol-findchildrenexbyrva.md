---
title: IDiaSymbol::findChildrenExByRVA | Dokumentace Microsoftu
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
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 001804a8e47f7870c61d869751165fc054997223
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736311"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte podřízené objekty daného symbolu, které jsou platné na zadaný relativní virtuální adrese (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `symtag`  
 [in] Určuje symbol značky podřízené položky, které se mají načíst, jak jsou definovány v [symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md). Nastavte na `SymTagNull` pro všechny podřízené objekty, které se mají načíst.  
  
 `name`  
 [in] Určuje název podřízenou položku, která se má načíst. Nastavte na `NULL` pro všechny podřízené objekty, které se mají načíst.  
  
 `compareFlags`  
 [in] Určení možností porovnání uplatňovat na odpovídající název. Hodnoty z [namesearchoptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md) výčtu lze použít samostatně nebo v kombinaci.  
  
 `address`  
 [in] Určuje, adresa RVA.  
  
 `ppResult`  
 [out] Vrátí [idiaenumsymbols –](../../debugger/debug-interface-access/idiaenumsymbols.md) načíst objekt, který obsahuje seznam podřízenými symboly.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` Pokud byl nalezen nejméně jeden podřízený prvek symbolu nebo vrátí `S_FALSE` Pokud nebyly nalezeny žádné podřízené položky; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Lokální symboly, které jsou vráceny zahrnovat informace o rozsahu za provozu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia100.dll  
  
## <a name="see-also"></a>Viz také  
 [Idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumsymbols –](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren –](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)




---
title: Idiasymbol::get_addresssection – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e62f6738d07b2f0e4463cd685bf3111cd7011a10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820018"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Načte část oddílu umístění adresu. Použít, když [locationtype – výčet](../../debugger/debug-interface-access/locationtype.md) je nastavena na `LocIsStatic`.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí část oddílu umístění služby adresu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Pro statické členy v externí knihovny DLL části vrácený touto metodou být 0, protože tato metoda spoléhá na získání člena virtuální adresy. Virtuálních adres jsou platné pouze tehdy, pokud [idiasession::put_loadaddress –](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metodu [idiasession –](../../debugger/debug-interface-access/idiasession.md) rozhraní setcodepage se zavolala s nenulový parametr zadání adresy načtení knihovny DLL.  
  
 Získání posunu částí adresy, volání [idiasymbol::get_addressoffset –](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) metody.  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Záhlaví:|dia2.h|  
|Verze:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Viz také  
 [Idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
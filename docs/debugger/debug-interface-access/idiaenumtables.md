---
title: Idiaenumtables – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4018b347b3fa6989a2dbd2116ac2c234ebfb70f8
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058084"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Provede výčet různých tabulky obsažené v datovém zdroji.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDiaEnumTables`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Načte [IEnumVARIANT rozhraní](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) verzi této enumerátor.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Načte počet tabulek.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Načte tabulku prostřednictvím index nebo název.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Načte zadaný počet tabulek v pořadí výčtu.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Přeskočí zadaný počet tabulek v posloupnosti výčtu.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Návrat na začátek v sekvenci výčtu.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Vytvoří enumerátor, který obsahuje stav výčtu jako aktuální enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní [idiasession::getenumtables –](../../debugger/debug-interface-access/idiasession-getenumtables.md) metoda.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat `IDiaEnumTables` rozhraní z relace. Více kompletní příklad, jak pomocí tabulky, najdete v článku [idiatable –](../../debugger/debug-interface-access/idiatable.md) rozhraní.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
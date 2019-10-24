---
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41679304986f5de948119a2958524b8f269ceb42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741924"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Načte enumerátor pro všechny tabulky obsažené v úložišti symbolů.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametry
`ppEnumTables`

mimo Vrátí objekt [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) . Pomocí tohoto rozhraní můžete vytvořit výčet tabulek v úložišti symbolů.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad
Tento příklad představuje obecnou funkci, která používá metodu `getEnumTables` k získání konkrétního objektu enumerátoru. Pokud je zjištěn enumerátor, funkce vrátí ukazatel, který lze přetypovat na požadované rozhraní; v opačném případě funkce vrátí `NULL`.

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Viz také:
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)

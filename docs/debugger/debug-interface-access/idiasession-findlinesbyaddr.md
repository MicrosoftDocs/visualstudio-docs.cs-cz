---
title: 'IDiaSession:: findLinesByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24c6d927d129a8005bf2e43c6bb69d6523cb8790
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465669"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
Načte řádky v zadaném kompilantu, které obsahují zadanou adresu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByAddr (
    DWORD                 seg,
    DWORD                 offset,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`seg`

pro Určuje komponentu oddílu konkrétní adresy.

`offset`

pro Určuje komponentu posunu konkrétní adresy.

`length`

pro Určuje počet bajtů rozsahu adres, které se mají pokrýt s tímto dotazem.

`ppResult`

mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje seznam všech čísel řádků, které pokrývají zadaný rozsah adres.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="example"></a>Příklad
Tento příklad ukazuje funkci, která získá všechna čísla řádků obsažená ve funkci pomocí adresy a délky funkce.

```C++
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,
                                          IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                seg;
    DWORD                offset;
    ULONGLONG            length;

    if (pFunc->get_addressSection ( &seg ) == S_OK &&
        pFunc->get_addressOffset ( &offset ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)

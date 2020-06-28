---
title: 'IDiaSession:: findLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5e39793e2060daebf93759feb9c64622a9cf880
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465578"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Načte informace o číslech řádků na řádcích obsažených v zadaném rozsahu virtuální adresy (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`va`

pro Určuje adresu jako VA.

`length`

pro Určuje počet bajtů rozsahu adres, které se mají pokrýt s tímto dotazem.

`ppResult`

mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje seznam všech čísel řádků, které pokrývají zadaný rozsah adres.

## <a name="example"></a>Příklad
Tento příklad ukazuje funkci, která získá všechna čísla řádků obsažená ve funkci pomocí virtuální adresy a délky funkce.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)

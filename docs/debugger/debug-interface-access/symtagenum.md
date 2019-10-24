---
title: SymTagEnum – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738518"
---
# <a name="symtagenum"></a>SymTagEnum
Určuje typ symbolu.

## <a name="syntax"></a>Syntaxe

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Elementy
`SymTagNull` označuje, že symbol nemá žádný typ.

`SymTagExe` označuje, že symbol je soubor. exe. Pro každé úložiště symbolů je k dispozici pouze jeden `SymTagExe` symbol. Slouží jako globální rozsah a nemá lexikální nadřazený objekt.

`SymTagCompiland` označuje symbol kompilantu pro každou součást kompilantu úložiště symbolů. Pro nativní aplikace `SymTagCompiland` symboly odpovídat objektovým souborům propojeným s imagí. U některých druhů imagí jazyka MSIL (Microsoft Intermediate Language) existuje jedna kompilantu na třídu.

`SymTagCompilandDetails` označuje, že symbol obsahuje rozšířené atributy kompilantu. Načítání těchto vlastností může vyžadovat načtení kompilantu symbolů.

`SymTagCompilandEnv` označuje, že symbol je řetězec prostředí definovaný pro kompilantu.

`SymTagFunction` označuje, že symbol je funkce.

`SymTagBlock` označuje, že symbol je vnořený blok.

`SymTagData` označuje, že symbol je data.

`SymTagAnnotation` označuje, že symbol je pro anotaci kódu. Podřízené objekty tohoto symbolu jsou konstantní datové řetězce (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Většina klientů tento symbol ignoruje.

`SymTagLabel` označuje, že symbol je popisek.

`SymTagPublicSymbol` označuje, že symbol je veřejný symbol. Pro nativní aplikace je tento symbol externí symbol COFF při propojování obrázku.

`SymTagUDT` označuje, že symbol je uživatelem definovaný typ (struktura, třída nebo sjednocení).

`SymTagEnum` označuje, že symbol je výčet.

`SymTagFunctionType` označuje, že symbol je typ podpisu funkce.

`SymTagPointerType` označuje, že symbol je typ ukazatele.

`SymTagArrayType` označuje, že symbol je typ pole.

`SymTagBaseType` označuje, že symbol je základní typ.

`SymTagTypedef` označuje, že symbol je `typedef`, to znamená, že alias pro jiný typ.

`SymTagBaseClass` označuje, že symbol je základní třídou uživatelsky definovaného typu.

`SymTagFriend` označuje, že symbol je přítelm uživatelsky definovaného typu.

`SymTagFunctionArgType` označuje, že symbol je argumentem funkce.

`SymTagFuncDebugStart` označuje, že symbol je koncové umístění kódu prologu funkce.

`SymTagFuncDebugEnd` označuje, že symbol představuje počáteční umístění epilogu kódu funkce.

`SymTagUsingNamespace` označuje, že symbol je název oboru názvů aktivní v aktuálním oboru.

`SymTagVTableShape` označuje, že symbol je popis virtuální tabulky.

`SymTagVTable` označuje, že symbol je ukazatel virtuální tabulky.

`SymTagCustom` označuje, že symbol je vlastní symbol a není interpretován pomocí DIA.

`SymTagThunk` označuje, že symbol je převod kódu, který se používá pro sdílení dat mezi 16 a 32 bitovým kódem.

`SymTagCustomType` označuje, že symbol je vlastní symbol kompilátoru.

`SymTagManagedType` označuje, že symbol je v metadatech.

`SymTagDimension` označuje, že symbol je multidimenzionální pole FORTRAN.

`SymTagCallSite` označuje, že symbol představuje web volání.

`SymTagInlineSite` označuje, že symbol představuje vloženou lokalitu.

`SymTagBaseInterface` označuje, že symbol je základní rozhraní.

`SymTagVectorType` označuje, že symbol je vektorový typ.

`SymTagMatrixType` označuje, že symbol je typ matice.

`SymTagHLSLType` označuje, že symbol je typ jazyka shaderu na vysoké úrovni.

## <a name="remarks"></a>Poznámky
Všechny symboly v souboru ladění mají identifikační značku, která určuje typ symbolu.

Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

Hodnoty v tomto výčtu jsou předány do následujících metod pro omezení rozsahu hledání na konkrétní typ symbolu:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

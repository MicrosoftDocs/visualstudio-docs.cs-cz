---
title: SymTagEnum – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 29bbb4eed485d3ff354757ab8c83a60b92f566aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461047"
---
# <a name="symtagenum"></a>SymTagEnum
Určuje typ symbolu.

## <a name="syntax"></a>Syntax

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
`SymTagNull` Indikuje, že symbol nemá žádný typ.

`SymTagExe` Označuje, že symbol je soubor. exe. Pro každé úložiště symbolů je k dispozici pouze jeden `SymTagExe` symbol. Slouží jako globální rozsah a nemá lexikální nadřazený objekt.

`SymTagCompiland` Označuje symbol kompilantu pro každou součást kompilantu úložiště symbolů. Pro nativní aplikace `SymTagCompiland` symboly odpovídají objektovým souborům, které jsou propojeny s obrázkem. U některých druhů imagí jazyka MSIL (Microsoft Intermediate Language) existuje jedna kompilantu na třídu.

`SymTagCompilandDetails` Indikuje, že symbol obsahuje rozšířené atributy kompilantu. Načítání těchto vlastností může vyžadovat načtení kompilantu symbolů.

`SymTagCompilandEnv` Označuje, že symbol je řetězec prostředí definovaný pro kompilantu.

`SymTagFunction` Indikuje, že symbol je funkce.

`SymTagBlock` Označuje, že symbol je vnořený blok.

`SymTagData` Označuje, že symbol je data.

`SymTagAnnotation` Označuje, že symbol je určen pro anotaci kódu. Podřízené objekty tohoto symbolu jsou konstantní datové řetězce ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). Většina klientů tento symbol ignoruje.

`SymTagLabel` Označuje, že symbol je popisek.

`SymTagPublicSymbol` Označuje, že symbol je veřejný symbol. Pro nativní aplikace je tento symbol externí symbol COFF při propojování obrázku.

`SymTagUDT` Označuje, že symbol je uživatelem definovaný typ (struktura, třída nebo sjednocení).

`SymTagEnum` Označuje, že symbol je výčet.

`SymTagFunctionType` Označuje, že symbol je typ podpisu funkce.

`SymTagPointerType` Označuje, že symbol je typ ukazatele.

`SymTagArrayType` Označuje, že symbol je typ pole.

`SymTagBaseType` Označuje, že symbol je základní typ.

`SymTagTypedef` Označuje, že symbol je `typedef` , to znamená, že alias pro jiný typ.

`SymTagBaseClass` Označuje, že symbol je základní třídou uživatelsky definovaného typu.

`SymTagFriend` Označuje, že symbol je přítelm uživatelsky definovaného typu.

`SymTagFunctionArgType` Označuje, že symbol je argumentem funkce.

`SymTagFuncDebugStart` Označuje, že symbol je koncové umístění kódu prologu funkce.

`SymTagFuncDebugEnd` Označuje, že symbol představuje počáteční umístění epilogu kódu funkce.

`SymTagUsingNamespace` Označuje, že symbol je název oboru názvů aktivní v aktuálním oboru.

`SymTagVTableShape` Indikuje, že symbol je popis virtuální tabulky.

`SymTagVTable` Indikuje, že symbol je ukazatel virtuální tabulky.

`SymTagCustom` Označuje, že symbol je vlastní symbol a není interpretován pomocí DIA.

`SymTagThunk` Označuje, že symbol je převod pomocí kódu, který se používá pro sdílení dat mezi 16 a 32 bitovým kódem.

`SymTagCustomType` Označuje, že symbol je vlastní symbol kompilátoru.

`SymTagManagedType` Označuje, že symbol je v metadatech.

`SymTagDimension` Označuje, že symbol je multidimenzionální pole FORTRAN.

`SymTagCallSite` Označuje, že symbol představuje web volání.

`SymTagInlineSite` Označuje, že symbol představuje vloženou lokalitu.

`SymTagBaseInterface` Označuje, že symbol je základní rozhraní.

`SymTagVectorType` Označuje, že symbol je vektorový typ.

`SymTagMatrixType` Označuje, že symbol je typ matice.

`SymTagHLSLType` Označuje, že symbol je typ jazyka shaderu na vysoké úrovni.

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

## <a name="see-also"></a>Viz také
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

---
title: IDebugComPlusSymbolProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733473"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Představuje poskytovatele symbolu MODELU COM+ s metodami, které jsou specifické pro spravovaný kód.

## <a name="syntax"></a>Syntaxe

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Přestože neexistuje žádné oddělení mezi rozhraní, které jsou užitečné pro vyhodnocení výrazu (EE) a ty, které jsou určeny k použití ladicí modul (DE), následující metody budou pravděpodobně zájem DE vývojáři pouze: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols, a UpdateSymbols.

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Určuje, zda jsou pro zadaný modul načteny ladicí symboly s diodou domény aplikace.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Vytvoří typ ze zadaného primitivního typu.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje pozici dokumentu v zadaném modulu na pole ladicích adres.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Načte informace o typu zadaného pole s jeho ladicí adresou.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Načte název sestavení dané jeho modul a doménu aplikace.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Načte třídy se zadaným atributem, které jsou implementovány v daném programovacím jazyce.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Načte třídy se zadaným atributem v daném modulu.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Načte vstupní bod aplikace.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Načte adresu v rámci funkce, která představuje odsazení daného řádku.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Načte rozložení místních proměnných pro sadu metod.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Vrátí název přidružený k zadanému tokenu, který je zadán jeho objektu metadat.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Načte symboly ladění s daným nadřazeným atributem pro zadaný modul.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Načte čtečku symbolů, která má být použita nespravovaným kódem.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Načte se na typ symbolu dané jeho ladicí adresu.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Určuje, zda je odstraněna funkce na zadané adrese ladění.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Určuje, zda je funkce na zadané adrese ladění považována za zastaralou.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Určuje, zda je kód na zadané adrese ladicího programu skrytý.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Načte zadané symboly ladění v paměti.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Načte ladicí symboly dané datového proudu.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Nahradí aktuální symboly ladění symboly v zadaném datovém proudu.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Uvolní ladicí symboly pro zadaný modul z paměti.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje ladicí symboly v paměti s těmi, zadaný datový proud.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

---
title: Rozhraní (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 902a3d361eb06288a0e50e9f384b67a2a8c61aa1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461271"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Rozhraní (Přístup k rozhraní ladění SDK)
Metody jsou seřazeny podle abecedy pod každým rozhraním v obsahu a na stránce rozhraní v pořadí podle tabulky vtable.

## <a name="in-this-section"></a>V tomto oddílu

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

Poskytuje kontrolu nad tím, jak DIA SDK počítá virtuální a relativní virtuální adresy pro objekty ladění.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Inicializuje přístup ke zdroji ladicích symbolů.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Poskytuje přístup k záznamům v datovém proudu ladění.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Vytvoří výčet různých streamů ladění obsažených ve zdroji dat.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Vytvoří výčet různých datových prvků rámce obsažených ve zdroji dat.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Vytvořte výčet různých vložených zdrojů obsažených ve zdroji dat.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Vytvoří výčet různých čísel řádků obsažených ve zdroji dat.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Vytvoří výčet různých příspěvků obsažených v části zdroje dat.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Vytvoří výčet různých segmentů obsažených ve zdroji dat.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Vytvoří výčet různých zdrojových souborů obsažených ve zdroji dat.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Vytvoří výčet různých dostupných rámců zásobníku.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Vytvoří výčet různých symbolů obsažených ve zdroji dat.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Provede výčet podle adres různých symbolů obsažených ve zdroji dat.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Vytvoří výčet různých tabulek obsažených ve zdroji dat.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Zpřístupňuje podrobnosti rámce zásobníku.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Zpřístupňuje podrobné informace o základním umístění a posunech paměti modulu nebo obrázku.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

Přistupuje ke zdrojovému kódu programu uloženému ve zdroji dat DIA.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Přistupuje k informacím, které popisují proces mapování z bloku bajtů textu obrázku na číslo řádku zdrojového souboru.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

Přijímá zpětná volání z procesu hledání symbolů DIA a umožňuje tak uživatelské rozhraní nahlásit průběh pokusu o umístění.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

Přijímá zpětná volání z procesu hledání symbolů DIA, což umožňuje, aby bylo omezení uloženo na proces vyhledávání.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Umožňuje číst trvalé vlastnosti sady vlastností DIA.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

Umožňuje klientské aplikaci poskytovat bajty spustitelného souboru, jak je uvedeno v umístění souboru.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Umožňuje klientské aplikaci poskytovat bajty spustitelného souboru, jak je určeno relativní virtuální adresou.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Načte data popisující příspěvek oddílu, to znamená, že souvislý blok paměti přispěl k obrázku pomocí kompilantu.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Mapuje data z čísla oddílu na segmenty adresního prostoru.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Poskytuje kontext dotazu pro symboly ladění.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Představuje zdrojový soubor.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Zpřístupňuje vlastnosti rámce zásobníku.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

Poskytuje metody pro procházení zásobníku pomocí souboru PDB.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

Udržuje kontext zásobníku mezi voláními metody [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Usnadňuje procházení zásobníku pomocí souboru PDB (program Debug Database).

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Popisuje vlastnosti instance symbolu.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Vytvoří výčet tabulky zdroje dat DIA.

## <a name="related-sections"></a>Související oddíly
[Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)

Popisuje výčty a struktury používané různými rozhraními DIA SDK.

[Konstanty (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

Popisuje konstanty, které jsou k dispozici v DIA SDK.

## <a name="see-also"></a>Viz také

- [Reference](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
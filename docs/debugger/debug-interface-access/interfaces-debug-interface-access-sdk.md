---
title: Rozhraní (přístup k rozhraní SDK ladění) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 584c7337ae50f85f95f063a47787b8a4be37c9fb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474739"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Rozhraní (Přístup k rozhraní ladění SDK)
Metody jsou abecední v rámci každé rozhraní v tabulce obsahu a na stránce rozhraní v tabulce Vtable pořadí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Umožňuje řídit způsob vypočítá DIA SDK virtuální a relativní virtuální adresy ladění objekty.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Iniciuje přístup k zdroj symboly ladění.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Poskytuje přístup k záznamům v datový proud ladění.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Vytvoří výčet různé datové proudy debug obsažené v datovém zdroji.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Vytvoří výčet různé datové prvky rámce obsažené v datovém zdroji.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Výčet různých vloženého zdrojů obsažené v datovém zdroji.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Provede výčet různých čísla řádků, které jsou obsažené v datovém zdroji.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Vytvoří výčet různé části příspěvky obsažené v datovém zdroji.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Provede výčet různých segmentů obsažené v datovém zdroji.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Provede výčet různých zdrojové soubory obsažené v datovém zdroji.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Provede výčet různých rámce zásobníku, která je k dispozici.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Provede výčet různých symboly obsažené v datovém zdroji.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Vytvoří výčet podle adresy různé symboly obsažené v datovém zdroji.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Provede výčet různých tabulky obsažené v datovém zdroji.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Zpřístupní podrobnosti rámce zásobníku.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Zpřístupní podrobnosti o základní umístění a paměť posunutí modulu nebo image.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Přístupy zdrojový kód aplikace uložené ve zdroji dat DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Informace přístupů, které popisuje proces mapování z bloku bajtů image textu číslo řádku zdrojového souboru.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Zpětná volání obdrží z symbol DIA postup vyhledání, čímž umožní uživatelské rozhraní hlásit průběh pokus o umístění.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Zpětná volání obdrží z symbol DIA postup vyhledání, která umožňují omezení uložená vyhledáním proces.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Umožňuje číst trvalé vlastnosti sady vlastností DIA.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Umožňuje aplikaci klienta k poskytování bajtů spustitelného souboru jako zadaný umístěním souboru.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Umožňuje aplikaci klienta k poskytování bajtů spustitelný soubor určený relativní virtuální adresu.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Načte data popisující část příspěvku, tedy blok souvislé paměti přispěli k bitové kopii kompilace.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mapuje dat z číslo oddílu segmenty adresního prostoru.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Poskytuje kontext dotazu pro symboly ladění.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Představuje zdrojového souboru.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Zpřístupní vlastnosti rámce zásobníku.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Poskytuje možnosti metod protokolů provede pomocí souboru PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Udržuje zásobník kontextu mezi volání [idiaframedata::Execute –](../../debugger/debug-interface-access/idiaframedata-execute.md) metoda.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Usnadňuje procházení zásobníku pomocí souboru databáze (PDB) ladicí program.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Popisuje vlastnosti instance symbolu.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Vytvoří výčet DIA data zdrojová tabulka.  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Popisuje, výčty a struktury využívané prostředím různé rozhraní DIA SDK.  
  
 [Konstanty (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Popisuje, k dispozici v sadě DIA SDK konstanty.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
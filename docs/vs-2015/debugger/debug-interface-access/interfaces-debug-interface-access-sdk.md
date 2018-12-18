---
title: Rozhraní (přístup k rozhraní SDK ladění) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d74f42008a76fb9b3f5ac6966ec01721bcb32cac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809334"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Rozhraní (Přístup k rozhraní ladění SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Metody abecedním pořadí v rámci každé rozhraní v tabulce obsahu a na stránce rozhraní v tabulce Vtable pořadí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Umožňuje řídit jak DIA SDK vypočítá virtuální a relativní virtuální adresy pro ladění objektů.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Iniciuje přístup ke zdroji symboly ladění.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Poskytuje přístup k záznamům v datovém proudu ladění.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Vytvoří výčet různé datové proudy debug obsažené ve zdroji dat.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Vytvoří výčet různé prvky rámce data obsažená ve zdroji dat.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Zobrazení výčtu různých vloženého zdroje obsažené ve zdroji dat.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Provede výčet různých čísla řádků, které jsou obsaženy ve zdroji dat.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Vytvoří výčet různé části příspěvků obsažené ve zdroji dat.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Provede výčet různých segmentů obsažené ve zdroji dat.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Provede výčet různých zdrojové soubory obsažené ve zdroji dat.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Provede výčet různých rámce zásobníku, která je k dispozici.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Provede výčet různých symboly obsažené ve zdroji dat.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Vytvoří výčet podle adresy různé symboly obsažené ve zdroji dat.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Provede výčet různých tabulky obsažené ve zdroji dat.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Poskytuje podrobnosti o rámec zásobníku.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Poskytuje podrobnosti o základní posuny umístění a paměti modulu nebo image.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Přístupy zdrojový kód aplikace uložené ve zdroji dat DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Přístupy informace, které popisují proces mapování z bloku bajty bitové kopie textu na číslo řádku zdrojového souboru.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Zpětná volání obdrží od symbolu DIA postup vyhledání, což umožní uživatelského rozhraní pro informování o průběhu pokus o umístění.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Zpětná volání obdrží od DIA symbol hledání proceduru, která umožňují omezení vynucená pro proces vyhledáním.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Umožňuje číst trvalou vlastnosti sady DIA vlastností.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Umožňuje klientské aplikaci slouží k poskytování bajtů spustitelného souboru jako zadaným umístěním souboru.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Umožňuje klientské aplikaci slouží k poskytování bajtů spustitelný soubor určený relativní virtuální adresu.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Načte data popisující oddíl příspěvek, to znamená, souvislý blok paměti přispěla do bitové kopie kompilace.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mapuje data z část čísla do segmentů adresního prostoru.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Poskytuje kontext dotazu pro symboly ladění.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Reprezentuje zdrojový soubor.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Zpřístupní vlastnosti rámec zásobníku.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Poskytuje metody, jak provést zásobníku vás pomocí souboru PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Zásobník kontextu mezi voláními udržuje [idiaframedata::Execute –](../../debugger/debug-interface-access/idiaframedata-execute.md) metody.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Usnadňuje procházení zásobníku pomocí programového souboru databáze (PDB) ladění.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Popisuje vlastnosti instance symbolu.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Vytvoří výčet tabulky zdroje dat DIA.  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Popisuje, výčty a struktury využívané prostředím různá rozhraní DIA SDK.  
  
 [Konstanty (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Popisuje, k dispozici v sadě DIA SDK konstanty.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)




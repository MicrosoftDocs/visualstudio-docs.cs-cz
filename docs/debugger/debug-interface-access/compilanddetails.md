---
title: Compilanddetails – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b1288a3bde1a8d17f40971744298adb1e1ecffb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468805"
---
# <a name="compilanddetails"></a>CompilandDetails
Informace o kompilace je rozdělená mezi symboly s `SymTagCompiland` značky (nízkou podrobnosti) a `SymTagCompilandDetails` značky (vysokou úroveň podrobností). `SymTagCompilandDetails` vyžaduje, načítání další symboly. Však nabízí širokou řadu informace o kompilace, která není k dispozici `SymTagCompiland` symbol.  
  
## <a name="properties"></a>Vlastnosti  
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.  
  
|Vlastnost|Datový typ|Popis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Číslo sestavení back endu kompilátoru.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Back-end hlavní číslo verze kompilátoru.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Číslo podverze back endu kompilátoru.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Název kompilátoru, která vytváří tento kompilace (pouze v DIA SDK V8.0 nebo novější).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` je-li upravit a pokračovat byly povoleny v kompilaci.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Číslo sestavení front-endu kompilátoru.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front-endu hlavní číslo verze kompilátoru.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Počet front-endu podverze kompilátoru.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Pokud tato kompilace má informace o ladění (pouze v DIA SDK V8.0 nebo novější).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Pokud tato kompilace obsahuje spravovaný kód (jenom v v8.0 DIA SDK nebo novější).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Pokud kompilace bylo kompilováno s [/GS (Kontrola zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check) přepínače kompilátoru (pouze v DIA SDK V8.0 nebo novější).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Pokud kompilace byla převedená z Common mezilehlá jazyk (CIL) kódu do nativního kódu.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Pokud byl zarovnán uživatelem definované typy (UDT) zadány některé hranic paměti (pouze v DIA SDK V8.0 nebo novější).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Pokud kompilace bylo kompilováno s [/hotpatch (vytvořit kopii opravitelnou za provozu)](/cpp/build/reference/hotpatch-create-hotpatchable-image) přepínače kompilátoru (pouze v v8.0 DIA SDK nebo novější).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Pokud kompilace bylo kompilováno s [/ltgc (vytváření kódu v době propojování)](/cpp/build/reference/ltcg-link-time-code-generation) přepínače kompilátoru (pouze v DIA SDK V8.0 nebo novější).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Hodnota TRUE, pokud kompilace Microsoft Intermediate Language (MSIL) modulu (pouze v v8.0 DIA SDK nebo novější).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Jazyk zdrojového kódu.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro souboru pro kompilaci.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID nadřazené lexikální symbolu.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platformy, na kterém byl kompilován souboru pro kompilaci (jeden z [CV_CPU_TYPE_e – výčet](../../debugger/debug-interface-access/cv-cpu-type-e.md) hodnoty).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagCompilandDetails` (jeden z [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md) hodnoty).|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátory často jsou dodávány ve formuláři označuje jako dvě průchodu kompilátoru; v některých verzí kompilátoru každém průchodu zpracovává jinou aplikací. Tyto jsou označovány jako kompilátory front-end a back-end, proto vlastnosti symbol čísel verzí back-end a front-endu.  
  
## <a name="see-also"></a>Viz také  
 [Kompilace](../../debugger/debug-interface-access/compiland.md)   
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
---
title: CompilandDetails | Microsoft Docs
description: Vyhledejte referenční informace o typu symbolu CompilandDetails (SymTagCompilandDetails) v rozhraní ladění sady Visual Studio pro přístup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04687eb58ecee2211f098c0f432afc28e0465305
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728779"
---
# <a name="compilanddetails"></a>CompilandDetails
Informace kompilantu jsou rozdělené mezi symboly `SymTagCompiland` značkou (nízká detail) a `SymTagCompilandDetails` značkou (s vysokou podrobnostcí). `SymTagCompilandDetails` poskytuje širokou informaci o kompilantu, která není k dispozici se `SymTagCompiland` symbolem.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Číslo buildu back-endu kompilátoru.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Číslo hlavní verze kompilátoru pro back-end.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Back-endové číslo verze kompilátoru.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Název kompilátoru, který vytvořil tuto kompilantu (jenom v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Pokud byla povolena možnost upravit a pokračovat při kompilaci.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Číslo sestavení front-endu kompilátoru.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Číslo hlavní verze kompilátoru pro front-end.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Číslo dílčí verze kompilátoru pro front-end.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Pokud má tento kompilantu informace o ladění (pouze v DIA SDK verze 8.0 nebo novější).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Pokud tento kompilantu obsahuje spravovaný kód (pouze v DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Pokud byl kompilantu kompilován pomocí přepínače kompilátoru [/GS (buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) (pouze V DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Pokud byl kompilantu převeden z kódu Common Intermediate Language (CIL) do nativního kódu.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Pokud byly uživatelsky definované typy (UDT) zarovnané na určitou určenou hranici paměti (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Pokud byl kompilantu zkompilován s přepínačem kompilátoru [/hotpatch (vytvořit opravitelnou za provozu image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (pouze v DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Pokud byl kompilantu zkompilován s přepínačem kompilátoru [/LTCG (generování kódu při propojování)](/cpp/build/reference/ltcg-link-time-code-generation) (pouze V DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, pokud je kompilantu modul jazyka MSIL (Microsoft Intermediate Language) (pouze v DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Jazyk zdrojového kódu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro kompilantu.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platforma, na které byl zkompilován kompilantu (jedna z hodnot [výčtu CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagCompilandDetails` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Poznámky
 Kompilátory často přicházejí ve formě označované jako kompilátor dvou Passes; v některých verzích kompilátoru se každý průchod zpracovává pomocí samostatného programu. Tyto jsou známé jako front-end a back-endové kompilátory, takže vlastnosti symbolu pro čísla back-end a front-end verzí.

## <a name="see-also"></a>Viz také
- [Kompilant](../../debugger/debug-interface-access/compiland.md)
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
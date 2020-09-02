---
title: CompilandDetails | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703004"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Informace kompilantu jsou rozdělené mezi symboly `SymTagCompiland` značkou (nízká detail) a `SymTagCompilandDetails` značkou (s vysokou podrobnostcí). `SymTagCompilandDetails` vyžaduje načtení dalších symbolů. Poskytuje ale velké množství informací o kompilantu, které není k dispozici u `SymTagCompiland` symbolu.  
  
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
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Pokud byl kompilantu kompilován pomocí přepínače kompilátoru [/GS (buffer Security Check)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) (pouze V DIA SDK v 8.0 nebo novějším).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Pokud byl kompilantu převeden z kódu Common Intermediate Language (CIL) do nativního kódu.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Pokud byly uživatelsky definované typy (UDT) zarovnané na určitou určenou hranici paměti (pouze v DIA SDK V 8.0 nebo novějším).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Pokud byl kompilantu zkompilován s přepínačem kompilátoru [/hotpatch (vytvořit opravitelnou za provozu image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) (pouze v DIA SDK v 8.0 nebo novějším).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Pokud byl kompilantu zkompilován s přepínačem kompilátoru [/LTCG (generování kódu při propojování)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) (pouze V DIA SDK v 8.0 nebo novějším).|  
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
 [Kompilantu](../../debugger/debug-interface-access/compiland.md)   
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

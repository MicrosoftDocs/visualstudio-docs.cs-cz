---
title: Compilanddetails – | Dokumentace Microsoftu
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
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e94993440a8fba4b215cb7a7b32f55f98475fb51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769062"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompilace informací je rozdělená mezi symboly s `SymTagCompiland` značky (nízké podrobnosti) a `SymTagCompilandDetails` značky (vysokou úroveň podrobností). `SymTagCompilandDetails` vyžaduje načítání dalších symbolů. Však nabízí celou řadu informací o souboru, který není k dispozici pro kompilaci `SymTagCompiland` symbol.  
  
## <a name="properties"></a>Vlastnosti  
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.  
  
|Vlastnost|Datový typ|Popis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Číslo sestavení back-end kompilátoru.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Back-end hlavní číslo verze kompilátoru.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Back-end vedlejší číslo verze kompilátoru.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Název kompilátoru, který vytváří tato kompilace (pouze v DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Pokud během kompilace byly povoleny funkce upravit a pokračovat.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Číslo sestavení front-endu kompilátoru.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front-endu hlavní číslo verze kompilátoru.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front-endu vedlejší číslo verze kompilátoru.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Pokud je tato kompilace ladicí informace (pouze v DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Pokud je tato kompilace obsahuje spravovaný kód (pouze v sadě DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Pokud kompilace byl kompilován s [/GS (Kontrola zabezpečení vyrovnávací paměti)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) přepínače kompilátoru (pouze v DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Pokud kompilace byla převedená z kódu Common Intermediate Language (CIL) do nativního kódu.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Pokud byla zarovnána uživatelem definované typy (UDT) některé zadané hranice paměti (pouze v DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Pokud kompilace byl kompilován s [/hotpatch (vytvoření Image vyměnitelné za provozu)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) přepínače kompilátoru (pouze v sadě DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Pokud kompilace byl kompilován s [parametru/LTCG (generování kódu při propojování odkaz)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) přepínače kompilátoru (pouze v DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, pokud kompilace je modul Microsoft Intermediate Language (MSIL) (pouze v sadě DIA SDK ve verzi 8.0 nebo novější).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Jazyk zdrojového kódu.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol souboru pro kompilaci.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID nadřazené lexikální symbolu.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platforma, na kterém byl kompilován kompilace (jeden z [cv_cpu_type_e – výčet](../../debugger/debug-interface-access/cv-cpu-type-e.md) hodnoty).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagCompilandDetails` (jeden z [symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md) hodnoty).|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátory často pocházejí ve formě říká kompilátoru dvoufázovou; v některých verzích kompilátoru každého průchodu zařizuje služba samostatné programu. Toto jsou známé jako front-endu a back-end kompilátory, proto symbol vlastnosti pro čísla verze back-end a front-endu.  
  
## <a name="see-also"></a>Viz také  
 [Kompilace](../../debugger/debug-interface-access/compiland.md)   
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)




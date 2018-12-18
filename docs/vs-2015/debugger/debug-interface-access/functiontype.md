---
title: Functiontype – | Dokumentace Microsoftu
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
- function signature
- FunctionType symbol
ms.assetid: 646a07e7-9d4f-4e21-95e3-3e403cdd4843
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 824fdcf47712096c42d82c0211bcf1efb5db61f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727931"
---
# <a name="functiontype"></a>FunctionType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Každý podpis jedinečné funkce je identifikovaná `SymTagFunctionType` symbol. Každý parametr je označen jako symbol podřízené třídy `SymTagFunctionArgType` značky.  
  
## <a name="properties"></a>Vlastnosti  
 V následující tabulce jsou uvedeny další platné vlastnosti pro tento typ symbolu.  
  
|Vlastnost|Datový typ|Popis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|`DWORD`|Jedna z hodnot [cv_call_e – výčet](../../debugger/debug-interface-access/cv-call-e.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Třídy tuto funkci (nebo metoda) je členem.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID symbolu nadřazené třídy.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Pokud funkce je označená jako konstanta.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Počet parametrů funkce.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol ohraničující kompilace.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID nadřazené lexikální symbolu.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|`IDiaSymbol*`|Typ ukazatele metody objektu, ("this").|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagFunctionType` (jeden z [symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md) hodnoty).|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`LONG`|Logických "Tento" likvidátor pro metodu.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol pro typ vrácené hodnoty.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID typu symbol.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Pokud je funkce nezarovnaných.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Pokud je funkce označena jako volatile.|  
  
## <a name="see-also"></a>Viz také  
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Cv_access_e – výčet](../../debugger/debug-interface-access/cv-access-e.md)   
 [FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)




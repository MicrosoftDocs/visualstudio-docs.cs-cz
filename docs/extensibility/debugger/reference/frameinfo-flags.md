---
title: FRAMEINFO_FLAGS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd2273e7ca2769c5dde43d1c29f08989503659f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949120"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Určuje informace, které se mají načíst informace o objektu rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Členové  
 FIF_FUNCNAME  
 Inicializace/použít `m_bstrFuncName` pole.  
  
 FIF_RETURNTYPE  
 Inicializace/použít `m_bstrReturnType` pole.  
  
 FIF_ARGS  
 Inicializace/použít `m_bstrArgs` pole.  
  
 FIF_LANGUAGE  
 Inicializace/použít `m_bstrLanguage` pole.  
  
 FIF_MODULE  
 Inicializace/použít `m_bstrModule` pole.  
  
 FIF_STACKRANGE  
 Inicializace/použít `m_addrMin` a `m_addrMax` (rozsah zásobníku) pole.  
  
 FIF_FRAME  
 Inicializace/použít `m_pFrame` pole.  
  
 FIF_DEBUGINFO  
 Inicializace/použít `m_fHasDebugInfo` pole.  
  
 FIF_STALECODE  
 Inicializace/použít `m_fStaleCode` pole.  
  
 FIF_ANNOTATEDFRAME  
 Inicializace/použít `m_fAnnotatedFrame` pole.  
  
 FIF_DEBUG_MODULEP  
 Inicializace/použít `m_pModule` pole.  
  
 FIF_FUNCNAME_FORMAT  
 Naformátuje název funkce. Výsledek se vrátí v `m_bstrFunName` pole a žádná další pole jsou vyplněna.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Přidá návratový typ `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS  
 Přidá argumenty, které mají `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_LANGUAGE  
 Přidá jazyk tak, aby `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_MODULE  
 Přidá název modulu, který se má `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_LINES  
 Přidá počet řádků `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_OFFSET  
 Přidá `m_bstrFuncName` pole Posun v bajtech od začátku řádku, pokud `FIF_FUNCNAME_LINES` je zadán. Pokud `FIF_FUNCNAME_LINES` není zadán, nebo pokud čísla řádků nejsou k dispozici, přidá posun v bajtech od začátku funkci.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Přidá typ každého argumentu funkce `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Přidá název každý argument funkce `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Přidá hodnotu každý argument funkce `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Přidá typ, název a hodnotu všech argumentů `m_bstrFuncName` pole.  
  
 FIF_ARGS_TYPES  
 Typy argumentů se načte a ve formátu.  
  
 FIF_ARGS_NAMES  
 Názvy argumentů se načte a ve formátu.  
  
 FIF_ARGS_VALUES  
 Hodnoty argumentů se načte a ve formátu.  
  
 FIF_ARGS_ALL  
 Načíst a formátování typu, názvu a hodnoty všech argumentů.  
  
 FIF_ARGS_NOFORMAT  
 Určuje, že argumenty nejsou ve formátu (například není přidat otevírací a zavírací závorky seznamu argumentů ani přidat oddělovač mezi argumenty).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Určuje, že při načítání hodnoty argumentů by neměl používat vyhodnocení funkce (vlastnost).  
  
 FIF_FILTER_NON_USER_CODE  
 Ladicí stroj je k filtrování rámce neuživatelský kód tak, že nejsou zahrnuty.  
  
 FIF_ARGS_NO_TOSTRING  
 Nepovolit `ToString()` funkce zkušební nebo formátování při vrácení argumenty funkce.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informace o snímcích byste získali z hostovaná doména aplikace, nikoli hostitelský proces.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky jsou předány [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) a [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metody k označení pole, která mají být inicializovány v [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strukturou nebo strukturami.  
  
 Tyto příznaky jsou také použity k označení polí s [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury jsou používány a platný, pokud vrátí strukturu. Tyto hodnoty lze kombinovat pomocí logické bitové `OR`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
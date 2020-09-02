---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e5a930e81ff1105ba93ce3c3cff10ee8bff2f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538431"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje informace, které se mají načíst o objektu rámce zásobníku.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
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
public enum enum_FRAMEINFO_FLAGS {  
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
 Inicializujte nebo použijte `m_bstrFuncName` pole.  
  
 FIF_RETURNTYPE  
 Inicializujte nebo použijte `m_bstrReturnType` pole.  
  
 FIF_ARGS  
 Inicializujte nebo použijte `m_bstrArgs` pole.  
  
 FIF_LANGUAGE  
 Inicializujte nebo použijte `m_bstrLanguage` pole.  
  
 FIF_MODULE  
 Inicializujte nebo použijte `m_bstrModule` pole.  
  
 FIF_STACKRANGE  
 Inicializujte nebo použijte `m_addrMin` `m_addrMax` pole a (rozsah zásobníku).  
  
 FIF_FRAME  
 Inicializujte nebo použijte `m_pFrame` pole.  
  
 FIF_DEBUGINFO  
 Inicializujte nebo použijte `m_fHasDebugInfo` pole.  
  
 FIF_STALECODE  
 Inicializujte nebo použijte `m_fStaleCode` pole.  
  
 FIF_ANNOTATEDFRAME  
 Inicializujte nebo použijte `m_fAnnotatedFrame` pole.  
  
 FIF_DEBUG_MODULEP  
 Inicializujte nebo použijte `m_pModule` pole.  
  
 FIF_FUNCNAME_FORMAT  
 Formátuje název funkce. Výsledek je vrácen v `m_bstrFunName` poli a žádné další pole nebudou vyplněna.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Přidá návratový typ do `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS  
 Přidá argumenty do `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_LANGUAGE  
 Přidá jazyk do `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_MODULE  
 Přidá název modulu do `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_LINES  
 Přidá do pole počet řádků `m_bstrFuncName` .  
  
 FIF_FUNCNAME_OFFSET  
 Přidá do `m_bstrFuncName` pole Posun v bajtech od začátku řádku, pokud `FIF_FUNCNAME_LINES` je zadaný. Pokud není `FIF_FUNCNAME_LINES` zadán, nebo pokud nejsou k dispozici čísla řádků, přidá posun v bajtech od začátku funkce.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Přidá do pole typ každého argumentu funkce `m_bstrFuncName` .  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Přidá do pole název každého argumentu funkce `m_bstrFuncName` .  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Přidá hodnotu každého argumentu funkce do `m_bstrFuncName` pole.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Přidá do pole typ, název a hodnotu všech argumentů `m_bstrFuncName` .  
  
 FIF_ARGS_TYPES  
 Typy argumentů se načítají a naformátují.  
  
 FIF_ARGS_NAMES  
 Názvy argumentů se načítají a naformátují.  
  
 FIF_ARGS_VALUES  
 Hodnoty argumentů se načítají a naformátují.  
  
 FIF_ARGS_ALL  
 Načte a naformátuje typ, název a hodnotu všech argumentů.  
  
 FIF_ARGS_NOFORMAT  
 Určuje, že argumenty nejsou formátovány (například Nepřidávat levou a pravou závorky kolem seznamu argumentů ani nesmí přidávat oddělovač mezi argumenty).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Určuje, že při načítání hodnot argumentů by se neměla používat vyhodnocení funkce (Property).  
  
 FIF_FILTER_NON_USER_CODE  
 Ladicí stroj je filtrovat rámce nesouvisející s uživatelským kódem, takže nejsou zahrnuty.  
  
 FIF_ARGS_NO_TOSTRING  
 `ToString()`Při vracení argumentů funkce nepovolujte vyhodnocení funkce ani formátování.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informace o snímku by se měly nacházet od hostované aplikační domény a nemusí být procesem hostování.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky jsou předány metodám [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) a [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) , aby označovaly, která pole se mají inicializovat ve struktuře nebo strukturách [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
 Tyto příznaky slouží také k označení toho, která pole struktury [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) jsou použita a platná při vrácení struktury. Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)

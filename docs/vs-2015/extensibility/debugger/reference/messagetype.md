---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547205"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje typ a důvod zprávy.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Členové  
 MT_OUTPUTSTRING  
 Indikuje, že se zpráva má odeslat do okna výstup. To se vzájemně vylučují `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Indikuje, že se zpráva má zobrazit v okně se zprávou. To se vzájemně vylučují `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Hodnota masky, která izoluje cíl zprávy.  
  
 MT_REASON_EXCEPTION  
 Indikuje, že se zobrazí okno se zprávou jako výsledek výjimky. To se vzájemně vylučují `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Indikuje, že se zobrazí okno se zprávou v důsledku povýšení zarážka s trasováním. To se vzájemně vylučuje `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Hodnota masky, která izoluje důvod zobrazené zprávy.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou vráceny z metod [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) a [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Jedna z hodnot důvodů může být kombinována s jednou z výstupních hodnot cíle s použitím bitového operátoru `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

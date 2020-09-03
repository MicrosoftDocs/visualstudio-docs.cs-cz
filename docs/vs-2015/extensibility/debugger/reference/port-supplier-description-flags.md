---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a66ff327659ab44958c412f6f5b1f4a6390de39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205039"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Definuje metadata, která lze načíst o dodavatele portu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;  
```  
  
```csharp  
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
```  
  
## <a name="terms"></a>Terminologie  
 PSDFLAG_SHOW_WARNING_ICON  
 Pokud je toto políčko zaškrtnuté, zobrazí se v uživatelském rozhraní ikona upozornění.  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je vrácen metodou [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)

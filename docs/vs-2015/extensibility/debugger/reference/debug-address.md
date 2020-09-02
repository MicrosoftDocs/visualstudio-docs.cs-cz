---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d001d29433573fedde3b4310f989667538b4b69c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822458"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato struktura představuje adresu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Terminologie  
 ulAppDomainID  
 ID procesu.  
  
 guidModule  
 Identifikátor GUID modulu, který obsahuje tuto adresu.  
  
 tokClass  
 Token identifikující třídu nebo typ této adresy.  
  
> [!NOTE]
> Tato hodnota je specifická pro poskytovatele symbolů, proto nemá žádný obecný význam, než jako identifikátor typu třídy.  
  
 Adresa  
 Struktura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , která obsahuje sjednocení struktur popisujících jednotlivé typy adres. Hodnota `addr` .`dwKind` pochází z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , který vysvětluje, jak se má sjednocení interpretovat.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předána metodě [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) , která má být vyplněna.  
  
 **Upozornění [pouze C++]**  
  
 Pokud `addr.dwKind` je `ADDRESS_KIND_METADATA_LOCAL` a pokud není `addr.addr.addrLocal.pLocal` hodnota null, musíte zavolat `Release` na ukazatel tokenu:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress –](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

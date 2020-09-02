---
title: Implementace a registrace dodavatele portu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824675"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementace a registrace dodavatele portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Role dodavatele portu je ke sledování a dodávání portů, které zase spravují procesy. V době, kdy je potřeba port vytvořit, se vytvoří instance dodavatele portu pomocí příkazu spolucreate s identifikátorem GUID dodavatele portu (Správce ladění relace [SDM] použije dodavatele portu vybraný uživatelem nebo dodavatel portu určený systémem projektu). Model SDM pak zavolá [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) , aby bylo možné zjistit, zda lze přidat porty. Pokud je možné přidat port, je požadován nový port voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) a předáním [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , který popisuje daný port. `AddPort` Vrátí nový port reprezentovaný rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Diskuse  
 Port je vytvořen dodavatelem portu, který je zase přidružen k počítači nebo ladicímu serveru. Server může vytvořit výčet svých dodavatelů portů prostřednictvím metody[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) a dodavatel portu může vytvořit výčet portů prostřednictvím metody [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Kromě typické registrace modelu COM se musí dodavatel portu zaregistrovat sám se sadou Visual Studio tak, že do určitých umístění registru umístí identifikátor CLSID a název. Pomocná funkce sady SDK s názvem `SetMetric` zpracovává tuto Chore: je volána jednou pro každou položku, která má být registrována, tedy:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Dodavatel portu zruší registraci sebe sama voláním `RemoveMetric` (další pomocnou funkci sady SDK) pro každou položku, která byla zaregistrována, tedy:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
> [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` a `RemoveMetric` jsou statické funkce definované v dbgmetric. h a kompilovány do ad2de. lib. `metrictypePortSupplier` `metricCLSID` `metricName` V dbgmetric. h jsou také definovány pomocníki, a.  
  
 Dodavatel portu může dodat svůj název a identifikátor GUID prostřednictvím metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) a [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)

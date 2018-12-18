---
title: Implementace a registrace dodavatele portu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3844d6beca76781f741bfbe0c6bff71923075d36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728940"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementace a registrace dodavatele portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Role dodavatele portu je ke sledování a dodávky porty, které pak spravujte procesy. V době, kdy je potřeba vytvořit port dodavatele portu je vytvořena instance pomocí CoCreate s identifikátorem GUID dodavatele portu (Správce ladění relace [SDM] používat dodavatele portu vybraný uživatel nebo dodavatele portu určené systém projektu). Pak zavolá SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) zobrazíte mohou být přidány žádné porty. Pokud port lze přidat, je nový port požadované voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) a předáním [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) port, který popisuje. `AddPort` vrátí nový port reprezentována [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) rozhraní.  
  
## <a name="discussion"></a>Diskuse  
 Port je vytvořené dodavatele portu, který zase souvisí s počítači nebo ladění serveru. Serveru můžete zobrazit výčet její dodavatelé portů prostřednictvím[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metoda a dodavatele portu můžete zobrazit výčet prostřednictvím jeho porty [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metoda.  
  
 Kromě typické registrace modelu COM dodavatele portu musí registrovat pomocí sady Visual Studio tak, že jeho identifikátor CLSID a název v konkrétním registru umístění. Pomocná funkce ladění sady SDK volat `SetMetric` zpracovává v tomto případě: se volá jednou pro každou položku k registraci, tedy:  
  
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
  
 Dodavatele portu zruší registraci sám voláním `RemoveMetric` (jinou funkci pomocné rutiny ladění SDK) s jednou registrací u každé položky, která byla zaregistrována takto:  
  
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
>  [Pomocníci sad SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` a `RemoveMetric` jsou statické funkce definované v dbgmetric.h a zkompilovány do ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, A `metricName` pomocné rutiny jsou také definovány v dbgmetric.h.  
  
 Dodavatele portu můžete zadat jeho název a identifikátor GUID prostřednictvím metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) a [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocníci sad SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)


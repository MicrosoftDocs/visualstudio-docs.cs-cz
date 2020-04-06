---
title: Provádění a registrace dodavatele přístavu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738530"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementace a registrace dodavatele portů
Úlohou dodavatele přístavu je sledovat a dodávat přístavy, které zase řídí procesy. Když je potřeba vytvořit port, vytvoří se vytvoření instance dodavatele portu pomocí funkce CoCreate s identifikátorem GUID dodavatele portu (správce ladění relace [SDM] použije dodavatele portu, kterého vybraný uživatel nebo dodavatele portu zadal projektový systém). SDM pak volá [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) a zjistěte, zda lze přidat nějaké porty. Pokud port lze přidat, nový port je požadováno voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) a předáním [IDebugPortRequest2,](../../extensibility/debugger/reference/idebugportrequest2.md) který popisuje port. `AddPort`vrátí nový port reprezentované rozhraním [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Diskuse
 Port je vytvořen dodavatelem portu, který je přidružen k počítači nebo ladicímu serveru. Server vyjmenovává své dodavatele portů prostřednictvím metody[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) a dodavatel portu vyjmenovává své porty prostřednictvím metody [EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 Kromě typické registrace com, dodavatel portu musí zaregistrovat sám v sadě Visual Studio umístěním jeho CLSID a název v konkrétních umístěních registru. Ladicí pomocná funkce sady SDK s názvem `SetMetric` zpracovává tuto funkci v chore: je volána jednou pro každou položku, která má být registrována, tedy:

```cpp
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

 Dodavatel portu zruší registraci `RemoveMetric` sám voláním (jiné ladění SDK pomocné funkce) jednou pro každou položku, která byla registrována, tedy:

```cpp
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
> Pomocné [spoje sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` a `RemoveMetric` jsou statické funkce definované v *souboru dbgmetric.h* a zkompilovány do *souboru ad2de.lib*. `metricCLSID`V `metrictypePortSupplier` `metricName` *souboru dbgmetric.h*jsou také definovány pomocníky a pomocníky .

 Dodavatel portu může zadat svůj název a identifikátor GUID prostřednictvím metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) a [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md).

## <a name="see-also"></a>Viz také
- [Implementace dodavatele portů](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Pomocné spoje sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Dodavatelé přístavů](../../extensibility/debugger/port-suppliers.md)

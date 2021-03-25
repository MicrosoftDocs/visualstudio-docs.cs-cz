---
title: Implementace a registrace dodavatele portu | Microsoft Docs
description: Naučte se implementovat a registrovat dodavatele portu, který sleduje a dodává porty, které spravují procesy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16c1738d4059468384df7ee2e882c20c8b5a0537
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059831"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementace a registrace dodavatele portu
Role dodavatele portu je ke sledování a dodávání portů, které zase spravují procesy. Pokud je potřeba vytvořit port, dodavatel portu se vytvoří pomocí spoluvytváření s identifikátorem GUID dodavatele portu (Správce ladění relace [SDM] bude používat dodavatele portu, který uživatel vybral, nebo dodavatel portu určený systémem projektu). Model SDM pak zavolá [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) a zjistí, jestli je možné přidat nějaké porty. Pokud je možné přidat port, je požadován nový port voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) a předáním [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , který popisuje daný port. `AddPort` Vrátí nový port reprezentovaný rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .

## <a name="discussion"></a>Diskuse
 Port je vytvořen dodavatelem portu, který je přidružen k počítači nebo ladicímu serveru. Server vytvoří výčet svých dodavatelů portů prostřednictvím metody[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) a dodavatel portu vytvoří výčet jeho portů prostřednictvím metody [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .

 Kromě typické registrace modelu COM se musí dodavatel portu zaregistrovat sám se sadou Visual Studio tak, že do určitých umístění registru umístí identifikátor CLSID a název. Pomocná funkce sady SDK s názvem `SetMetric` zpracovává tuto Chore: je volána jednou pro každou položku, která má být registrována, tedy:

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

 Dodavatel portu zruší registraci sebe sama voláním `RemoveMetric` (další pomocnou funkci sady SDK) pro každou položku, která byla zaregistrována, tedy:

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
> [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` a `RemoveMetric` jsou statické funkce definované v *dbgmetric. h* a kompilovány do *ad2de. lib*. `metrictypePortSupplier` `metricCLSID` `metricName` V *dbgmetric. h* jsou také definovány pomocníki, a.

 Dodavatel portu může dodat svůj název a identifikátor GUID prostřednictvím metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) a [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)v uvedeném pořadí.

## <a name="see-also"></a>Viz také
- [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)

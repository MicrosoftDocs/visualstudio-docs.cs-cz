---
title: Implementace dodavatele přístavu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738552"
---
# <a name="implement-a-port-supplier"></a>Implementace dodavatele portů
Dodavatel portu dodává porty na vyžádání správci ladění relace (SDM). Dodavatel portu musí být implementován při ladění počítače bez dcom nebo když nové zařízení vyžaduje podporu. Chcete-li například zajistit ladění mobilního telefonu, můžete nastavit dodavatele portů, který poskytuje porty, které se připojují k mobilnímu telefonu (například prostřednictvím infračerveného přenosu nebo připojení k buňce) a vytvoří výčet procesů a programů spuštěných v telefonu.

 Pro ladění programů v počítačích se systémem Windows (včetně vzdáleného ladění) visual studio poskytuje dodavatele portů pro procesy nativního a běžného jazyka Runtime (CLR), takže v těchto případech není nutné nastavovat vlastního dodavatele portů.

## <a name="in-this-section"></a>V tomto oddílu
 [Implementace a registrace dodavatele portů](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Popisuje, jak s. M spolupracuje s dodavatelem portu a jeho porty.

 [Požadovaná rozhraní dodavatele portů](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentuje rozhraní, která je nutné implementovat, abyste získali dodavatele portu.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní ladění architektonických konceptů.

## <a name="see-also"></a>Viz také
 [Rozšiřitelnost ladicího programu visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

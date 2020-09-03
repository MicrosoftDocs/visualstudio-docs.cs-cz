---
title: Implementace dodavatele portu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738552"
---
# <a name="implement-a-port-supplier"></a>Implementace dodavatele portu
Dodavatel portu dodává porty na žádost do Správce ladění relace (SDM). Dodavatel portu se musí implementovat při ladění na počítač, který není typu DCOM, nebo když nové zařízení vyžaduje podporu. Chcete-li například poskytnout ladění na mobilní telefon, můžete nastavit dodavatele portu, který poskytuje porty, které se připojují k mobilnímu telefonu (například pomocí INFRAČERVENého připojení nebo připojení k buňce) a vyčísluje procesy a programy běžící na telefonu.

 Pro ladění programů na počítačích se systémem Windows (včetně vzdáleného ladění) poskytuje Visual Studio dodavatelům portů pro nativní procesy a procesy modulu CLR (Common Language Runtime), takže v těchto případech není nutné nastavovat vlastního dodavatele portu.

## <a name="in-this-section"></a>V této části
 [Implementace a registrace dodavatele portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Popisuje, jak model SDM komunikuje s dodavatelem portu a jeho porty.

 [Požadovaná rozhraní dodavatele portu](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentuje rozhraní, která je nutné implementovat pro získání dodavatele portu.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

## <a name="see-also"></a>Viz také
 [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

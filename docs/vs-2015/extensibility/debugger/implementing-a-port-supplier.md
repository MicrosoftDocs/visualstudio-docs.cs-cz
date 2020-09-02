---
title: Implementace dodavatele portu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152677"
---
# <a name="implementing-a-port-supplier"></a>Implementace dodavatele portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodavatel portu dodává porty na žádost do Správce ladění relace (SDM). Dodavatel portu se musí implementovat při ladění na jiný počítač než DCOM nebo v případě, že je potřeba podporovat nové zařízení. Chcete-li například poskytnout ladění na mobilní telefon, můžete implementovat dodavatele portu, který poskytuje porty, které se připojují k mobilnímu telefonu (například pomocí INFRAČERVENého připojení nebo připojení k buňce), a vyčísluje procesy a programy běžící na telefonu.  
  
 Pro ladění programů na počítačích se systémem Windows (včetně vzdáleného ladění) poskytuje Visual Studio dodavatelům portů pro nativní procesy a procesy modulu CLR (Common Language Runtime), takže v těchto případech není nutné implementovat vlastního dodavatele portu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace a registrace dodavatele portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Popisuje, jak model SDM komunikuje s dodavatelem portu a jeho porty.  
  
 [Požadovaná rozhraní dodavatele portu](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumentuje rozhraní, která musí být implementovaná, aby získala dodavatele portu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty architektury ladění.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

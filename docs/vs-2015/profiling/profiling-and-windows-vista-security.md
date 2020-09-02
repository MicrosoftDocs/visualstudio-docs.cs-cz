---
title: Profilace a zabezpečení systému Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7e485bc6289634e1bb6d4b4106d54c8dc82096b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683705"
---
# <a name="profiling-and-windows-vista-security"></a>Profilace a zabezpečení systému Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V závislosti na [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] nastavení uživatelských oprávnění přístupu, které správce počítače zpřístupnil, může mít jednotliví uživatelé oprávnění zabezpečení k profilování procesu na tomto počítači. Následující příklady ilustrují možné rozdíly mezi uživateli:  
  
- Někteří uživatelé mají přístup k pokročilým funkcím profilování, když správce nastavil ovladač a službu tak, aby se spouštěly.  
  
- Uživatelé domény mohou přistupovat pouze ke vzorové profilaci.  
  
- Někteří uživatelé můžou odepřít přístup k profilaci všem ostatním uživatelům.  
  
  Další informace najdete v tématu možnosti správy v [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Profilace mezi jednotlivými relacemi  
 Profilování *mezi jednotlivými relacemi* je schopnost profilovat proces, který běží v jiné přihlašovací relaci. Například většina služeb běží v relaci 0 a uživatelé nemohou běžet přímo v relaci 0. Pomocí tlačítka **připojit k procesu** na panelu nástrojů prohlížeč výkonu nebo možnosti/attach nástroje příkazového řádku VSPerfCmd můžete profilovat většinu procesů v různých přihlašovacích relacích.  
  
 Můžete zobrazit seznam procesů, které jsou k dispozici, nastavením možností viditelnosti mezi procesy. Tyto možnosti jsou k dispozici v okně **připojit k procesu** , které se zobrazí po kliknutí na **připojit k procesu**:  
  
- **Zobrazit procesy všech uživatelů**  
  
     Pokud tato možnost není vybrána, zobrazí se v seznamu pouze procesy vlastněné aktuálním uživatelem. Když je vybrána možnost **Zobrazit procesy všech uživatelů** , zobrazí seznam procesy všech uživatelů.  
  
- **Zobrazit procesy ve všech relacích**  
  
     Pokud tato možnost není vybraná, zobrazí se v seznamu procesy v aktuální relaci. Pokud je vybrána tato možnost, zobrazí se v seznamu procesy ve všech relacích.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Postupy: připojení ke spuštěnému procesu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)

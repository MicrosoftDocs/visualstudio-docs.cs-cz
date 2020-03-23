---
title: Profilování a zabezpečení systému Windows Vista | Dokumenty společnosti Microsoft
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2a74862d59fe402cbfd9e6bfa804d62ca4c8310b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778372"
---
# <a name="profiling-and-windows-vista-security"></a>Profilace a zabezpečení systému Windows Vista

V závislosti [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] na nastavení oprávnění k přístupu uživatelů, které správce počítače zpřístupnil, může mít jednotlivý uživatel oprávnění zabezpečení k profilování procesu v tomto počítači. Následující příklady ilustrují možné rozdíly mezi uživateli:

- Někteří uživatelé mohou získat přístup k pokročilým funkcím profilování, pokud správce nastavil spuštění ovladače a služby.

- Uživatelé domény mohou přistupovat pouze k profilování vzorků.

- Někteří uživatelé mohou odepřít přístup k profilování všem ostatním uživatelům.

  Další informace naleznete v možnostech ADMIN v [vsperfcmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilování mezi relacemi

*Profilování mezi relacemi* je možnost profilování procesu, který běží v jiné relaci uživatele. Například většina služeb běží v relaci 0 a uživatelé nemohou spustit přímo v relaci 0. Pomocí tlačítka **Připojit k procesu** na panelu `/attach` nástrojů Průzkumníka výkonu nebo možnosti nástroje příkazového řádku VSPerfCmd můžete profilovat většinu procesů v různých uživatelských relacích.

Seznam procesů, které jsou k dispozici, můžete zobrazit nastavením možností viditelnosti profilování mezi procesy. Tyto možnosti jsou k dispozici v okně **Připojit ke procesu,** které se zobrazí, když vyberete **Připojit k procesu**:

- **Zobrazit procesy od všech uživatelů**

  Pokud tato možnost není vybrána, seznam zobrazí pouze ty procesy, které jsou vlastněny aktuálním uživatelem. V opačném případě seznam zobrazí procesy od všech uživatelů.

- **Zobrazit procesy ve všech relacích**

  Pokud tato možnost není vybrána, seznam zobrazí procesy v aktuální relaci. V opačném případě seznam zobrazí procesy ve všech relacích.

## <a name="see-also"></a>Viz také

- [Přehledy](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Postup: Připojení ke spuštěnému procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))

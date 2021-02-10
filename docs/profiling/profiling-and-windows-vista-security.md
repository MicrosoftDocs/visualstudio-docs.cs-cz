---
title: Profilace a zabezpečení systému Windows Vista | Microsoft Docs
description: V závislosti na nastavení oprávnění k přístupu uživatele, která jsou k dispozici, může mít jednotliví uživatelé oprávnění zabezpečení k profilování procesu na daném počítači.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0419ae09f2b43b396062fc8a3232b0a63c81483c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936389"
---
# <a name="profiling-and-windows-vista-security"></a>Profilace a zabezpečení systému Windows Vista

V závislosti na [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] nastavení uživatelských oprávnění přístupu, které správce počítače zpřístupnil, může mít jednotliví uživatelé oprávnění zabezpečení k profilování procesu na tomto počítači. Následující příklady ilustrují možné rozdíly mezi uživateli:

- Někteří uživatelé mají přístup k pokročilým funkcím profilování, když správce nastavil ovladač a službu tak, aby se spouštěly.

- Uživatelé domény mohou přistupovat pouze ke vzorové profilaci.

- Někteří uživatelé můžou odepřít přístup k profilaci všem ostatním uživatelům.

  Další informace najdete v tématu možnosti správy v [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilace mezi jednotlivými relacemi

Profilování *mezi jednotlivými relacemi* je schopnost profilovat proces, který běží v jiné uživatelské relaci. Například většina služeb běží v relaci 0 a uživatelé nemůžou běžet přímo v relaci 0. Pomocí tlačítka **připojit k procesu** na panelu nástrojů prohlížeč výkonu nebo `/attach` Možnosti nástroje příkazového řádku VSPerfCmd můžete profilovat většinu procesů v různých uživatelských relacích.

Můžete zobrazit seznam procesů, které jsou k dispozici, nastavením možností viditelnosti mezi procesy. Tyto možnosti jsou k dispozici v okně **připojit k procesu** , které se zobrazí po výběru možnosti **připojit k procesu**:

- **Zobrazit procesy všech uživatelů**

  Pokud tato možnost není vybraná, zobrazí se v seznamu jenom procesy vlastněné aktuálním uživatelem. V opačném případě se v seznamu zobrazí procesy všech uživatelů.

- **Zobrazit procesy ve všech relacích**

  Pokud tato možnost není vybraná, zobrazí se v seznamu procesy v aktuální relaci. V opačném případě se v seznamu zobrazí procesy ve všech relacích.

## <a name="see-also"></a>Viz také

- [Přehledy](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Postupy: připojení ke spuštěnému procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))

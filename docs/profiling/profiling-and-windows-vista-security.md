---
title: Profilace a zabezpečení Windows Vista | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 767210a934753dd85b22728813d7608618a2b8d3
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220648"
---
# <a name="profiling-and-windows-vista-security"></a>Profilace a zabezpečení systému Windows Vista

V závislosti na tom [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] přístupová oprávnění uživatelů nastavení, které správce má k dispozici, individuální uživatel může mít oprávnění zabezpečení, chcete-li Profilovat procesy v tomto počítači. Následující příklady znázorňují možné rozdíly mezi uživateli:

- Někteří uživatelé mohou přístup k rozšířeným funkcím profilace, pokud správce nastavil ovladač a spouštění služby.

- Uživatelé domény mohou přistupovat k pouze profilace vzorku.

- Někteří uživatelé mohou odepřít přístup k profilaci a všem ostatním uživatelům.

  Další informace najdete v tématu Možnosti správce v [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilace mezi relacemi

*Mezi relacemi profilace* je schopnost Profilovat proces, na kterém běží v relaci jiného uživatele. Například většina služeb spuštěné v relaci 0, a uživatelé nemůžou spouštět přímo v relaci 0. S použitím **připojit k procesu** tlačítko na panelu nástrojů prohlížeče výkonu nebo `/attach` – možnost nástroje VSPerfCmd příkazového řádku, můžete provádět profilaci většina procesů v různých uživatelských relací.

Zobrazí se seznam procesů, které jsou k dispozici nastavením možností profilace viditelnost napříč procesy. Tyto možnosti jsou dostupné v **připojit k procesu** okno, které se zobrazí, když vyberete **připojit k procesu**:

- **Zobrazit procesy všech uživatelů**

  Pokud není vybraná tato možnost, v seznamu zobrazí pouze procesy, které jsou vlastněny aktuálního uživatele. V opačném případě se v seznamu zobrazí procesy všech uživatelů.

- **Zobrazit procesy ve všech relacích**

  Pokud není vybraná tato možnost, v seznamu zobrazí procesy v aktuální relaci. V opačném případě se v seznamu zobrazí procesy ve všech relacích.

## <a name="see-also"></a>Viz také:

- [Přehledy](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Postupy: připojení ke spuštěnému procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))

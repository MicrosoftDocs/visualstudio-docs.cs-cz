---
title: Řešení potíží s metrikami kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef7078b09b1bf2382e1c91878995772d80bfa625
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853958"
---
# <a name="troubleshooting-code-metrics-issues"></a>Řešení potíží s metrikami kódu
Některé z těchto problémů může dojít při shromažďování metrik kódu:

-   [Změny ve výpočtech složitost kódu sady Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Změny ve výpočtech složitost kódu sady Visual Studio 2010
 Pro stejnou funkci počítá metrika složitost kódu v [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] může lišit od metrika počítá v předchozích verzích [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] v těchto situacích:

- Funkce obsahuje jeden nebo více bloky catch. V předchozích verzích [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch bloky nebyly zahrnutých do výpočtu. V [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], složitost každého bloku catch se přidá do složitost funkce.

- Funkce obsahuje příkaz switch (Select Case v jazyce Visual Basic). Kompilátor rozdíly mezi [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] a starší verze můžete vygenerovat různé kód jazyka MSIL pro některé příkazů přepínače, které obsahují propuštěním případy.

## <a name="see-also"></a>Viz také
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
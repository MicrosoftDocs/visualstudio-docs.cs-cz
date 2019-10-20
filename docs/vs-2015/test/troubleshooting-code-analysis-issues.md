---
title: Řešení potíží s analýzou kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4eee70b3184496e8dbb7d784501a5cac2aac00ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672119"
---
# <a name="troubleshooting-code-analysis-issues"></a>Řešení potíží s Analýzou kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje informace o řešení potíží pro následující problémy analýzy kódu sady Visual Studio.

- [Změny v sadě pravidel sady Visual Studio 2010 se neprojeví v předchozích verzích sady Visual Studio.](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a>Změny v sadě pravidel sady Visual Studio 2010 se neprojeví v předchozích verzích sady Visual Studio.

Když vytvoříte sadu pravidel v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], která obsahuje sadu podřízených pravidel, změna podřízené sady pravidel se nemusí použít při spuštění analýzy kódu na počítačích, které používají starší verzi sady Visual Studio. Chcete-li tento problém vyřešit, je nutné vynutit přepsání sady nadřazených pravidel, což je sada pravidel, která obsahuje sadu podřízených pravidel.

1. Otevřete nadřazenou sadu pravidel v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].

2. Proveďte změnu, například přidání nebo odebrání pravidla, a potom sadu pravidel uložte.

3. Znovu otevřete sadu pravidel, převratte změnu a znovu uložte sadu pravidel.

## <a name="see-also"></a>Viz také:

- [Analýza kvality aplikace](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)
- [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Použití sad pravidel k seskupování pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)

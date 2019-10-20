---
title: 'Postupy: Určení sad pravidel spravovaného kódu pro více projektů v řešení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656426"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Postupy: Určení sad pravidel spravovaného kódu pro více projektů v určitém řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení se všechny spravované projekty řešení přiřazují do *sady pravidel*Microsoft minima pravidla analýzy kódu. Můžete změnit sady pravidel, které jsou přiřazeny k projektům řešení v dialogovém okně Vlastnosti pro dané řešení.

> [!NOTE]
> Ve výchozím nastavení není analýza kódu projektu spuštěna jako krok sestavení. Chcete-li povolit analýzu kódu jako krok sestavení, přečtěte si téma [Postupy: konfigurace analýzy kódu pro projekt spravovaného kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Určení sady pravidel pro více projektů v řešení spravovaného kódu

1. V [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] nebo [!INCLUDE[vsPro](../includes/vspro-md.md)] otevřete řešení.

2. V nabídce **analyzovat** klikněte na možnost **Konfigurovat analýzu kódu pro řešení**.

3. V případě potřeby rozbalte **společné vlastnosti**a pak klikněte na **nastavení analýzy kódu**.

4. Pro jeden nebo více projektů můžete zadat sadu pravidel.

    - Chcete-li zadat sadu pravidel pro jednotlivé projekty, klikněte na název projektu.

    - Chcete-li zadat sadu pravidel pro více projektů, podržte stisknutou klávesu CTRL a klikněte na název projektu.

    - Chcete-li zadat všechny projekty v řešení, podržte klávesu SHIFT a klikněte v seznamu projektu.

5. Klikněte na pole **sada pravidel** projektu a pak klikněte na název sady pravidel, kterou chcete použít.

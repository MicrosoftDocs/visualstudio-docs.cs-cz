---
title: 'Postupy: Změna oboru názvů jazyka specifického pro doménu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671722"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Postupy: Změna oboru názvů jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit obor názvů jazyka specifického pro doménu. Změnu je třeba provést v **Průzkumníkovi DSL**ve vlastnostech projektu balíčku DSL a v informacích o sestavení.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Změna oboru názvů jazyka specifického pro doménu

1. V **Průzkumníku DSL**klikněte na uzel **DSL** .

2. V okně **vlastnosti** změňte vlastnost **Namespace** .

3. Uložte řešení a Transformujte šablony.

4. V nabídce **projekt** klikněte na **vlastnosti DSL**.

     Zobrazí se vlastnosti projektu.

5. Klikněte na kartu **aplikace** .

6. Změňte **výchozí vlastnost Namespace** na název nového oboru názvů.

7. Pokud chcete také změnit název sestavení, změňte **vlastnost název sestavení.**

8. Pokud jste změnili název sestavení, otevřete DslPackage\Package.tt a aktualizujte tento řádek:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Pokud jste napsali vlastní kód, nezapomeňte změnit obor názvů a odkazy na třídy v souborech kódu.

10. Resetovat experimentální instanci sady Visual Studio.

    1. Odstraňte **\Users \\ **_{Name}_**\AppData\Local\Microsoft\VisualStudio \\ \* exp**

    2. V nabídce **Start** systému Windows vyberte **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a **obnovte experimentální instanci**.

11. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

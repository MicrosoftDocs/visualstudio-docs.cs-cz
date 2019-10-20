---
title: 'Postupy: Změna oboru názvů jazyka specifického pro doménu'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653773"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Postupy: Změna oboru názvů jazyka specifického pro doménu

Můžete změnit obor názvů jazyka specifického pro doménu. Proveďte změnu v **Průzkumníkovi DSL**ve vlastnostech projektu balíčku DSL a v informacích o sestavení.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Změna oboru názvů jazyka specifického pro doménu

1. V **Průzkumníku DSL**vyberte uzel **DSL** .

2. V okně **vlastnosti** změňte vlastnost **Namespace** .

3. Uložte řešení a Transformujte šablony.

4. V nabídce **projekt** vyberte **vlastnosti DSL**.

   Zobrazí se vlastnosti projektu.

5. Vyberte kartu **aplikace** .

6. Změňte **výchozí vlastnost Namespace** na název nového oboru názvů.

7. Pokud chcete také změnit název sestavení, změňte **vlastnost název sestavení.**

8. Pokud jste změnili název sestavení, otevřete DslPackage\Package.tt a aktualizujte tento řádek:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Pokud jste napsali vlastní kód, nezapomeňte změnit obor názvů a odkazy na třídy v souborech kódu.

10. Resetovat experimentální instanci sady Visual Studio.

    1. Odstraňte **\\** \AppData\Local\Microsoft\VisualStudio _{name}_ **\\ \*Exp**.

    2. V nabídce **Start** systému Windows vyberte **všechny programy**  > **Microsoft Visual Studio 2010 SDK**  > **Tools**  > **obnovení experimentální instance**.

11. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

## <a name="see-also"></a>Viz také:

[Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
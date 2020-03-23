---
title: 'Návod: Použití api profileru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 81071a44b51b1441782b25741126873fc720ed7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779880"
---
# <a name="walkthrough-using-profiler-apis"></a>Návod: Použití rozhraní API profileru

Návod používá aplikaci Jazyka C# k [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] předvedení použití nástrojů profilování API. Pomocí api profileru omezíte množství dat shromážděných během profilování instrumentace.

 Kroky v tomto návodu obecně platí pro aplikaci C/C++. Pro každý jazyk budete muset odpovídajícím způsobem nakonfigurovat prostředí sestavení.

 Obvykle začnete analyzovat výkon aplikace pomocí profilování vzorků. Pokud profilování vzorku neposkytuje informace, které určuje kritické místo, instrumentace profilování může poskytnout vyšší úroveň podrobností. Instrumentace profilování je velmi užitečné pro zkoumání interakce vlákna.

 Větší úroveň podrobností však znamená, že je shromažďováno více dat. Můžete zjistit, že profilování instrumentace vytváří velké datové soubory. Také instrumentace je pravděpodobnější, že vliv na výkon aplikace. Další informace naleznete [v tématu Principy hodnot dat instrumentace](../profiling/understanding-instrumentation-data-values.md) a [Principy hodnot vzorkovacích dat.](../profiling/understanding-sampling-data-values.md)

 Profilování sady Visual Studio umožňuje omezit shromažďování dat. Tento návod nabízí příklad, jak omezit shromažďování dat pomocí api profileru. Profiler sady Visual Studio poskytuje rozhraní API pro řízení shromažďování dat z aplikace.

 ::: moniker range="vs-2017"
 Pro nativní kód jsou v *souboru VSPerf.dll*. Soubor záhlaví *VSPerf.h*a knihovna importu *VSPerf.lib*jsou umístěny v adresáři *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK.*  U 64bitových aplikací je složka *Microsoft Visual Studio\2017\Týmové nástroje\Nástroje výkonu\x64\PerfSDK*
 ::: moniker-end

 Pro spravovaný kód jsou rozhraní API profileru v *souboru Microsoft.VisualStudio.Profiler.dll*. Tato dll byla nalezena v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.* U 64bitových aplikací je složka *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Další informace naleznete v tématu [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Požadavky
 Tento návod předpokládá, že vaše volba vývojového prostředí je nakonfigurována tak, aby podporovala ladění a vzorkování. Následující témata poskytují přehled těchto předpokladů:

- [Postup: Zvolte metody kolekce](../profiling/how-to-choose-collection-methods.md)

- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Ve výchozím nastavení při spuštění profileru profiler shromažďuje data na globální úrovni. Následující kód na začátku programu vypne globální profilování.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Shromažďování dat na příkazovém řádku můžete vypnout bez použití volání rozhraní API. Následující kroky předpokládají, že prostředí sestavení příkazového řádku je nakonfigurováno tak, aby spouštěli nástroje profilování a jako vývojové nástroje. To zahrnuje nastavení nezbytné pro VSInstr a VSPerfCmd. Viz [Nástroje pro profilování příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="limit-data-collection-using-profiler-apis"></a>Omezit shromažďování dat pomocí api profileru

#### <a name="to-create-the-code-to-profile"></a>Vytvoření kódu do profilu

1. Vytvořte nový projekt Jazyka C# v sadě Visual Studio nebo použijte sestavení příkazového řádku v závislosti na vašich preferencích.

    > [!NOTE]
    > Sestavení musí odkazovat na knihovnu *Microsoft.VisualStudio.Profiler.dll* umístěnou v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.*

2. Zkopírujte a vložte do projektu následující kód:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication1
    {
        class Program
        {
            public class A
            {
                private int _x;

                public A(int x)
                {
                    _x = x;
                }

                public int DoNotProfileThis()
                {
                    return _x * _x;
                }

                public int OnlyProfileThis()
                {
                    return _x + _x;
                }

                public static void Main()
                {
                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    A a = new A(2);
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis());

                    DataCollection.StartProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    int x;
                    x = a.OnlyProfileThis();

                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    Console.WriteLine("2 doubled is {0}", x);
                }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Shromažďování a zobrazení dat v sadě IDE sady Visual Studio

1. Otevřete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide. V nabídce **Analyzovat** přejděte na **Profiler**a pak vyberte **Nová relace výkonu**.

2. Přidejte zkompilovaný binární soubor do seznamu **Cíle** v okně **Průzkumník výkonu.** Klepněte pravým tlačítkem myši na **cíl a**potom vyberte přidat cílový **binární soubor**. Vyhledejte binární soubor v dialogovém okně **Přidat cílový binární** soubor a klepněte na tlačítko **Otevřít**.

3. Ze seznamu **Metoda** na panelu nástrojů **Průzkumník výkonu** vyberte **Instrumentace.**

4. Klepněte na **tlačítko Spustit s profilováním**.

    Profiler bude instrumentovat a spustit binární soubor a vytvořit soubor sestavy výkonu. Soubor sestavy výkonu se zobrazí v uzlu **Sestavy** **Průzkumníka výkonu**.

5. Otevřete výsledný soubor sestavy výkonu.

   Ve výchozím nastavení při spuštění profileru bude profiler shromažďovat data na globální úrovni. Následující kód na začátku programu vypne globální profilování.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Shromažďování a zobrazení dat na příkazovém řádku

1. Zkompilujte ladicí verzi ukázkového kódu, který jste vytvořili v postupu "Vytvoření kódu do profilu", dříve v tomto návodu.

2. Chcete-li profilovat spravovanou aplikaci, zadejte následující příkaz, který nastaví příslušné proměnné prostředí:

     **VsPerfCLREnv /traceon**

3. Zadejte následující příkaz: **Název \<souboru VSInstr>.exe**

4. Zadejte následující příkaz: **VSPerfCmd /start:trace /output:\<název_souboru>.vsp**

5. Zadejte následující příkaz: **VSPerfCmd /globaloff**

6. Spusťte program.

7. Zadejte následující příkaz: **VSPerfCmd /shutdown**

8. Zadejte následující příkaz: **VSPerfReport\</calltrace: název souboru>.vsp**

     A. *csv* soubor je vytvořen v aktuálním adresáři s výslednými údaji o výkonu.

## <a name="see-also"></a>Viz také

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Začínáme](../profiling/getting-started-with-performance-tools.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)

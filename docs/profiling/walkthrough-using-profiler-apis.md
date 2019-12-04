---
title: 'Návod: použití rozhraní API profileru | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779880"
---
# <a name="walkthrough-using-profiler-apis"></a>Návod: Použití rozhraní API profileru

Návod používá C# aplikaci k demonstraci způsobu použití rozhraní api [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci. K omezení množství dat shromážděných během profilace instrumentace budete používat rozhraní API profileru.

 Kroky v tomto návodu se obecně vztahují na jazyk C/C++ aplikace. Pro každý jazyk bude nutné odpovídajícím způsobem nakonfigurovat prostředí sestavení.

 Obvykle se začne analyzovat výkon aplikace pomocí ukázkové profilace. Pokud ukázka profilace neposkytuje informace, které odhalují kritický bod, může profilace instrumentace poskytnout větší úroveň podrobností. Profilace instrumentace je velmi užitečná pro zkoumání interakce vlákna.

 Vyšší úroveň podrobností ale znamená, že se shromažďují další data. Může se stát, že profilace instrumentace vytváří soubory s velkými objemy dat. Instrumentace je také pravděpodobnější, že má vliv na výkon aplikace. Další informace najdete v tématu [vysvětlení hodnot dat instrumentace](../profiling/understanding-instrumentation-data-values.md) a [porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md) .

 Profiler sady Visual Studio umožňuje omezit shromažďování dat. Tento názorný postup nabízí příklad, jak omezit shromažďování dat pomocí rozhraní API profileru. Profiler sady Visual Studio poskytuje rozhraní API pro řízení shromažďování dat v rámci aplikace.

 ::: moniker range="vs-2017"
 V případě nativního kódu jsou rozhraní API profileru sady Visual Studio v *knihovně VSPerf. dll*. Hlavičkový soubor, *VSPerf. h*a knihovna importů *VSPerf. lib*, jsou umístěny v adresáři *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .  Pro 64-bitové aplikace je to složka *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 Pro spravovaný kód jsou rozhraní API profileru v *knihovně Microsoft. VisualStudio. Profiler. dll*. Tato knihovna DLL se nachází v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* . Pro 64 aplikace je tato složka *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Další informace najdete v tématu [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Požadavky
 Tento návod předpokládá, že vaše volba vývojového prostředí je nakonfigurovaná tak, aby podporovala ladění a vzorkování. Následující témata obsahují přehled těchto požadavků:

- [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)

- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Ve výchozím nastavení, když je profiler spuštěný, Profiler shromáždí data na globální úrovni. Následující kód na začátku programu zapne globální profilování.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Shromažďování dat můžete vypnout na příkazovém řádku bez použití volání rozhraní API. Následující postup předpokládá, že vaše prostředí pro sestavení příkazového řádku je nakonfigurované tak, aby spouštělo nástroje pro profilaci a jako vývojové nástroje. To zahrnuje nastavení potřebná pro VSInstr a VSPerfCmd. Viz [nástroje příkazového řádku pro profilaci](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="limit-data-collection-using-profiler-apis"></a>Omezení shromažďování dat pomocí rozhraní API profileru

#### <a name="to-create-the-code-to-profile"></a>Vytvoření kódu pro profilaci

1. Vytvořte nový C# projekt v aplikaci Visual Studio nebo použijte sestavení příkazového řádku, a to v závislosti na vaší předvolbách.

    > [!NOTE]
    > Vaše sestavení musí odkazovat na knihovnu *Microsoft. VisualStudio. Profiler. dll* , která se nachází v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

2. Zkopírujte a vložte následující kód do projektu:

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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Shromažďování a zobrazování dat v integrovaném vývojovém prostředí sady Visual Studio

1. Otevřete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). V nabídce **analyzovat** přejděte na **Profiler**a pak vyberte **Nová výkonnostní relace**.

2. Přidejte kompilovaný binární soubor do seznamu **cílů** v okně **prohlížeč výkonu** . Klikněte pravým tlačítkem na možnost **cíle**a pak vyberte **Přidat cílový binární soubor**. V dialogovém okně **Přidat cílový binární soubor** vyhledejte binární soubor a klikněte na tlačítko **otevřít**.

3. V seznamu **Metoda** na panelu nástrojů **prohlížeč výkonu** vyberte **instrumentace** .

4. Klikněte na **Spustit s profilací**.

    Profiler instrumentuje a spustí binární soubor a vytvoří soubor sestavy výkonu. Soubor sestavy o výkonu se zobrazí v uzlu **sestavy** **prohlížeč výkonu**.

5. Otevřete výsledný soubor sestavy výkonu.

   Ve výchozím nastavení se při spuštění profileru bude Profiler shromažďovat data na globální úrovni. Následující kód na začátku programu zapne globální profilování.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Shromažďování a zobrazování dat na příkazovém řádku

1. Zkompilujte ladicí verzi ukázkového kódu, který jste vytvořili v postupu "vytvoření kódu pro profilování" dříve v tomto návodu.

2. Chcete-li nastavit profil spravované aplikace, zadejte následující příkaz pro nastavení příslušných proměnných prostředí:

     **VsPerfCLREnv/TRACEON**

3. Zadejte následující příkaz: **VSInstr \<filename >. exe**

4. Zadejte následující příkaz: **VSPerfCmd/Start: Trace/output:\<filename >. vsp**

5. Zadejte následující příkaz: **VSPerfCmd/globaloff**

6. Spusťte program.

7. Zadejte následující příkaz: **VSPerfCmd/shutdown**

8. Zadejte následující příkaz: **VSPerfReport/calltrace:\<filename >. vsp**

     Určitého. v aktuálním adresáři se vytvoří soubor *CSV* s výslednými daty o výkonu.

## <a name="see-also"></a>Viz také:

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Začínáme](../profiling/getting-started-with-performance-tools.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)

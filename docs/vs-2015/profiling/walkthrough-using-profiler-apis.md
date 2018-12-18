---
title: 'Návod: Použití rozhraní API Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab545d338defb3876145c8ac648574484fbf89a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749082"
---
# <a name="walkthrough-using-profiler-apis"></a>Návod: Použití rozhraní API profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návod používá k ukazují, jak používat aplikace v jazyce C# [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profilování rozhraní API nástroje. Chcete-li omezit množství dat shromážděných během profilace instrumentace použijete rozhraní API profileru.  
  
 Kroky v tomto názorném postupu se obecně používají pro aplikace v jazyce C/C++. Pro každý jazyk musíte správně nakonfigurovat prostředí sestavení.  
  
 Obvykle se začnou analýze výkonu aplikace pomocí profilace vzorku. Pokud profilace vzorku neposkytuje informace, které zjišťuje kritickým bodem, profilace instrumentace může poskytnout vyšší úroveň podrobností. Profilace instrumentace je velmi užitečný k prošetření interakce vlákna.  
  
 Vyšší úroveň podrobností znamená, že se shromažďují další data. Můžete zjistit, že profilace instrumentace vytvoří velkých datových souborů. Instrumentace je navíc pravděpodobnější dopad na výkon aplikace. Další informace najdete v tématu [porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md) a [porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)  
  
 Profiler sady Visual Studio umožňuje omezit shromažďování dat o. Tento návod poskytuje příklad toho, jak omezit shromažďování dat pomocí rozhraní API profileru. Profiler sady Visual Studio poskytuje rozhraní API pro řízení shromažďování dat z v rámci aplikace.  
  
 Pro nativní kód profileru sady Visual Studio rozhraní API jsou v VSPerf.dll. Soubor hlaviček, VSPerf.h a knihovnu importu VSPerf.lib, jsou umístěny v adresáři nástroje nástroje 9\Team sady Microsoft Visual Studio.  
  
 Pro spravovaný kód, profiler rozhraní API jsou v Microsoft.VisualStudio.Profiler.dll. Tato knihovna DLL je najde v adresáři sady Microsoft Visual Studio 9\Team nástroje nástroje. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento názorný průvodce předpokládá, že vývojové prostředí podle vašeho výběru je nakonfigurována pro podporu ladění a vzorkování. Přehled o těchto nezbytných podmínkách naleznete v následujících tématech:  
  
 [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)  
  
 [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Ve výchozím nastavení při spuštění profilování, profiler shromáždí data na globální úrovni. Následující kód při spuštění programu se změní na globální profilace vypnout.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Bez použití volání rozhraní API můžete vypnout shromažďování dat na příkazovém řádku. Následující postup předpokládá, že vaše prostředí pro sestavení příkazového řádku je nakonfigurován na spuštění nástrojů pro profilaci a jako vývojové nástroje. To zahrnuje nastavení požadovaná pro nástroj VSInstr a VSPerfCmd. Zobrazit nástroje pro profilaci příkazového řádku.  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Omezení shromažďování dat pomocí rozhraní API Profiler  
  
#### <a name="to-create-the-code-to-profile"></a>Chcete-li vytvořit kód pro profil  
  
1.  Vytvořte nový projekt C# v sadě Visual Studio nebo pomocí příkazového řádku sestavení, v závislosti na vašich předvoleb.  
  
    > [!NOTE]
    >  Sestavení musí odkazovat na knihovnu Microsoft.VisualStudio.Profiler.dll umístěn v adresáři 9\Team nástroje nástroje sady Microsoft Visual Studio.  
  
2.  Zkopírujte a vložte následující kód do vašeho projektu:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
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
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
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
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Můžete shromažďovat a zobrazovat data v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Otevřít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí. K **analyzovat** nabídky, přejděte k **Profiler**a pak vyberte **nová výkonnostní relace.**  
  
2. Přidat kompilované binární soubor na **cíle** v seznamu **prohlížeč výkonu** okna. Klikněte pravým tlačítkem na **cíle**a pak vyberte **přidat cílový binární**. Vyhledejte příslušný binární soubor v **přidat cílový binární** dialogové okno a potom klikněte na **otevřít**.  
  
3. Vyberte **instrumentace** z **metoda** seznamu **prohlížeč výkonu** nástrojů.  
  
4. Klikněte na tlačítko **spustit s nástrojem pro profilaci**.  
  
    Profileru instrumentace a spustí binárního souboru a vytvoření souboru sestavy výkonu. Zobrazí se v souboru obsahujícímu sestavu výkonu **sestavy** uzlu **prohlížeč výkonu**.  
  
5. Otevřete výsledného souboru obsahujícímu sestavu výkonu.  
  
   Ve výchozím nastavení při spuštění profileru, profiler shromáždí data na globální úrovni. Následující kód při spuštění programu se změní na globální profilace vypnout.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Můžete shromažďovat a zobrazovat data na příkazovém řádku  
  
1.  Zkompilujte ladicí verze ukázek kódu, který jste vytvořili v postupu "Vytvoření kódu pro profil" dříve v tomto návodu.  
  
2.  Chcete-li Profilovat spravované aplikace, zadejte následující příkaz nastavit příslušné proměnné prostředí:  
  
     **VsPefCLREnv /traceon**  
  
3.  Zadejte následující příkaz:**VSInstr \<název souboru > .exe**  
  
4.  Zadejte následující příkaz:**/start:trace VSPerfCmd/output:\<název souboru > .vsp**  
  
5.  Zadejte následující příkaz:**VSPerfCmd /globaloff**  
  
6.  Spuštění programu.  
  
7.  Zadejte následující příkaz:**VSPerfCmd/Shutdown**  
  
8.  Zadejte následující příkaz:**VSPerfReport/calltrace:\<název souboru > .vsp**  
  
     Soubor CSV se vytvoří v aktuálním adresáři s Výsledná data o výkonu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Reference k rozhraní API sady Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Začínáme se službou](../profiling/getting-started-with-performance-tools.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)




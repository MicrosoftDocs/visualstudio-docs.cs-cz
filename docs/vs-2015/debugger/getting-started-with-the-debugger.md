---
title: Začínáme s ladicím programem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202320"
---
# <a name="getting-started-with-the-debugger"></a>Začínáme s ladicím programem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio se snadno používá v jakémkoli jazyce. Tady ukážeme, jak ladit jednoduchý program v jazyce C#, ale stejný postup můžete použít pro kód v jiných jazycích, jako je C++ a JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Ladění základního projektu C#  
 Podíváme se na jednoduchou konzolovou aplikaci v jazyce C# (**soubor/nový/projekt**, pak vyberte **Visual C#** a pak vyberte **Konzolová aplikace**). Pokud jste ještě nikdy nepracovali se sadou Visual Studio, přečtěte si [Návod: Vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Metoda **Main** pouze přičte 1 k celočíselné proměnné desetkrát a výsledek vytiskne do konzoly:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Sestavte tento kód v konfiguraci **ladění** . Tato konfigurace je standardně nastavená. Další informace o konfiguracích naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).  
  
 Spusťte tento kód v ladicím programu kliknutím na **ladění/spustit ladění** (nebo **Spusťte** na panelu nástrojů nebo **F5**). Aplikace by se měla ukončit téměř okamžitě, takže nebudete ve skutečnosti vědět, jestli se cokoli v okně konzoly vytisklo.  
  
 Běh můžete zastavit dostatečně dlouho, aby se zobrazilo okno konzoly nastavením zarážky a následnou krok dopředu. Chcete-li nastavit zarážku, umístěte kurzor na `Console.WriteLine` řádek a klikněte na možnost **ladění/novou zarážku/funkce**nebo pouze klikněte na levý okraj na stejném řádku. Zarážka by měla vypadat takto:  
  
 ![Nastavení zarážky](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Další informace o zarážekch naleznete v tématu [using zarážek](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Kontrola proměnných  
 Ladění často zahrnuje hledání proměnných, které neobsahují očekávané hodnoty v určitém bodě. Zobrazíme některé způsoby, jak můžete zkontrolovat proměnné.  
  
 Spusťte ladění znovu. Spuštění se zastaví, než se `Console.WriteLine` spustí kód. Můžete to provést v krok dopředu (klikněte na **ladit/krokovat přes** nebo **F10**). V takovém případě můžete zvolit **Krok do** (**F11**) a stejného výsledku. Tento rozdíl vyvysvětlíme později. Čára, která má poslední složenou závorku metody, by měla být zapnula žlutě. Podívejte se na okno konzoly. Mělo by se zobrazit **10**.  
  
 Pomocí ukazatele na **testInt** můžete zobrazit aktuální hodnotu v tipu dat.  
  
 ![DBG&#95;základy&#95;ch tipů pro&#95;dat](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Hned pod oknem kód byste měli vidět okna **Automatické**hodnoty, **místní**hodnoty a **kukátko** . Tato okna zobrazují aktuální hodnoty proměnných v době provádění. Okna **auto** a **místní** hodnoty zobrazují **testInt** s hodnotou **10**.  
  
 ![Okno Automatické hodnoty při ladění](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Další informace o těchto oknech najdete v tématu [Automatická a místní okna](../debugger/autos-and-locals-windows.md).  
  
 Pojďme se podívat, jak se hodnota proměnné mění při procházení programem. Nastavte zarážku na `testInt += 1;` řádku a znovu spusťte ladění. Měli byste vidět, **že testInt** v **oknech místní** hodnoty a **Automatické** hodnoty je **0**a **1**. **i** Když budete pokračovat v ladění (**ladění/pokračování**nebo **pokračovat** na panelu nástrojů nebo **F5**), vidíte, že se hodnota **testInt** změní na **1**, pak na **2**atd. Až se už vás unavuje na tyto změny, odeberte zarážku (**ladění/přepínací zarážku**nebo klikněte na ni na okraji) a pokračujte v ladění. Chcete-li odebrat všechny zarážky, klikněte na položku **ladit/odstranit všechny zarážky**nebo **CTRL + SHIFT + F9**a v dialogovém okně, které se zobrazí, klikněte na tlačítko **Ano** . chcete **Odstranit všechny zarážky?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Rozkrokování volání funkcí a přes ně  
 Můžete spustit kód v příkazu ladicího programu – podle příkazu (**Krokovat do**) nebo můžete spustit kód, zatímco ladicí program přeskočí funkce (**Krokovat**s vnořením), abyste se rychle dostali do kódu, o který se zajímáte (kód funkce je stále spuštěný). Mezi oběma metodami můžete přepínat ve stejné relaci ladění.  
  
 Chcete-li zobrazit rozdíl mezi **krokem do** a **krokování**, musíme přidat metodu, která je volána jinou metodou. Přidejte metodu do aplikace jazyka C# a zavolejte ji z metody Main. Kód by měl vypadat přibližně takto:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Nastavte zarážku v `Method1();` volání metody Main a spusťte ladění. Po přerušení provádění klikněte na položku **ladit/krokovat** s vnořením (nebo **Krok do** panelu nástrojů nebo **F11**). Provádění se znovu zalomí u první složené závorky v – Metoda1 ():  
  
 ![Krokování do kódu](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Zastavte ladění a začněte znovu a po přerušení provádění na zarážce klikněte na tlačítko **ladění/krokování** (nebo **krokování** ) na panelu nástrojů nebo **F10**. Provádění se znovu zruší v `Console.WriteLine("end");` .  
  
 Pokud chcete získat další informace o procházení kódu pomocí ladicího programu, přečtěte si téma [Navigace kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

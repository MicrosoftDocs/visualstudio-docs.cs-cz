---
title: Začínáme s ladicím programem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: 755c4a0b66c91aa37f96d3d6f06972878ee856b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771612"
---
# <a name="getting-started-with-the-debugger"></a>Začínáme s ladicím programem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio je snadno použitelné v jakémkoli jazyce. Tady vám ukážeme, jak ladit jednoduchý program C#, ale stejný postup můžete použít ke kódu v jiných jazycích, jako je například C++ a JavaScript.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Ladění projektu základního jazyka C#  
 Začněme jednoduchou aplikaci konzoly C# (**soubor / nový / Project**a pak vyberte **Visual C#** a pak vyberte **konzolovou aplikaci**). Pokud jste nikdy nepracovali s Visual Studio před, naleznete v tématu [návod: vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). **Hlavní** metoda právě přičte 1 k celočíselná proměnná 10krát a vytiskne výsledek do konzoly:  
  
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
  
 Vytvořit tento kód **ladění** konfigurace. Tato konfigurace je ve výchozím nastavení. Další informace o konfiguracích najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).  
  
 Tento kód spustit v ladicím programu kliknutím **ladění / spuštění ladění** (nebo **Start** na panelu nástrojů nebo **F5**). Aplikace by měla téměř okamžitě ukončena, proto nelze ve skutečnosti zjistit, zda nic byl vytištěn v okně konzoly.  
  
 Můžete zastavit provádění dostatečně dlouho najdete v okně konzoly nastavením zarážky a pak krokování dopředu. Nastavit zarážku, umístěte kurzor `Console.WriteLine` řádku a klikněte na tlačítko **ladění / Nová zarážka / zarážky funkce**, nebo stačí kliknout na levý okraj na stejném řádku. Zarážka by měl vypadat nějak takto:  
  
 ![Nastavit zarážku](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Další informace o zarážkách najdete v tématu [pomocí zarážek](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Kontrolovat proměnné  
 Ladění často zahrnuje hledání proměnné, které neobsahují hodnoty, které očekáváte, že v určitém místě. Vám ukážeme některé ze způsobů, můžete kontrolovat proměnné.  
  
 Znovu spusťte ladění. Provádění zastaví před `Console.WriteLine` spustí kód. Může způsobit to provést pomocí procházení dopředu (klikněte na tlačítko **ladění / krok přes** nebo **F10**). V tomto případě může zvolení **Krokovat s vnořením** (**F11**) a mohli stejný výsledek; dále vysvětlíme rozdíl. Řádek s poslední složená závorka metody by měly obracejí žlutou. Podívejte se na okno konzoly. Měli byste vidět **10**.  
  
 Najedete myší **testInt** proměnné v popisu dat zobrazit aktuální hodnotu.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Pod okna kódu by se měla zobrazit **automatické hodnoty**, **lokální**, a **Watch** systému windows. Tato okna zobrazit aktuální hodnoty proměnných v době spuštění. Oba **automatické hodnoty** a **lokální** windows zobrazit **testInt** s hodnotou **10**.  
  
 ![Okno Automatické hodnoty při ladění](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Další informace o těchto oken naleznete v tématu [automatické hodnoty a místní hodnoty Windows](../debugger/autos-and-locals-windows.md).  
  
 Podívejme se, jak mění hodnotu proměnné, které vás provedeme procesem program. Nastavit zarážku na `testInt += 1;` řádku a znovu spusťte ladění. Byste měli vidět, který **testInt** v **lokální** a **automatické hodnoty** windows je **0**, a **můžu** je **1**. Když budete pokračovat v ladění (**ladění / Continue**, nebo **pokračovat** na panelu nástrojů nebo **F5**), vidíme, že hodnota **testInt** změny **1**, pak **2**, a tak dále. Když dostanete unaveným z pohledu na tyto změny, odeberte zarážku (**ladění / Přepnout zarážku**, nebo klikněte na něj na okraji) a pokračovat v ladění. Pokud chcete odebrat všechny zarážky, klikněte na tlačítko **ladění / odstranit všechny zarážky**, nebo **CTRL + SHIFT + F9**a klikněte na tlačítko **Ano** v dialogovém okně s dotazem **je dostupná Chcete odebrat všechny zarážky?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Krokování do a přes volání funkce  
 Může spustit kód v ladicí program příkazu by-– příkaz (**Krokovat s vnořením**) nebo může spustit kód, zatímco funkce přeskočí ladicího programu (**Krokovat s přeskočením**) rychlé kódu, že jste více zajímá, () Kód funkce stále provádí). Můžete přepínat mezi obě metody ve stejné relaci ladění.  
  
 Pokud chcete zobrazit rozdíl mezi **Krokovat s vnořením** a **Krokovat s přeskočením**, je potřeba přidat metodu, která volá jinou metodu. Přidání metody do aplikace C# a jeho volání z metodu Main. Kód by měl vypadat přibližně takto:  
  
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
  
 Nastavit zarážku na `Method1();` volání do metody Main a spusťte ladění. Při provádění přeruší, klikněte na tlačítko **ladění / Krokovat s vnořením** (nebo **Krokovat s vnořením** na panelu nástrojů nebo **F11**). Spuštění konce znovu na první složená závorka v Method1():  
  
 ![Krokování s vnořením do kódu](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Zastavit ladění a začít znovu a při provádění zastaví u zarážky, klikněte na tlačítko **ladění / krok přes** (nebo **Krokovat s přeskočením** na panelu nástrojů nebo **F10**). Spuštění znovu zasekne při `Console.WriteLine("end");`.  
  
 Pokud chcete získat další informace o navigace v kódu s ladicím programem, najdete v článku [procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).






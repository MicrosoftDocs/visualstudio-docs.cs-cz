---
title: Ladění v době návrhu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9c4b0996faf26279ff8018e0e072fd25a33d783
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063419"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Ladění v době návrhu v sadě Visual Studio (C#, C++, Visual Basic, F#)

Postup ladění kódu v době návrhu namísto při aplikace běží, můžete použít **okamžité** okna. 

Postup ladění kódu XAML za aplikace z Návrháře XAML, jako je například data vazební kód, můžete použít **ladění** > **připojit k procesu**.
  
## <a name="use-the-immediate-window"></a>Použijte příkazové podokno  

Můžete použít Visual Studio **okamžité** okna spuštění funkce nebo podprogram bez spuštění vaší aplikace. Pokud funkce nebo podprogram obsahuje zarážku, sada Visual Studio přeruší na zarážce. Potom můžete ladicí program windows prozkoumat stav vaší aplikace. Tato funkce se nazývá *ladění v době návrhu*.  

V následujícím příkladu je v jazyce Visual Basic. Můžete také použít **okamžité** okno v době návrhu v C#, F#a aplikací v jazyce C++.

1. Následující kód vložte do prázdné konzolové aplikace jazyka Visual Basic:  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. Nastavit zarážku na řádku **End Function**.  
   
1. Otevřít **okamžité** okna tak, že vyberete **ladění** > **Windows** > **okamžité**. Typ `?MyFunction` , a poté stiskněte klávesu **Enter**.   
   
   Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **1**. Když je aplikace v režimu pozastavení můžete prozkoumat zásobník volání a dalších oknech ladění. 
   
1. Vyberte **pokračovat** na panelu nástrojů sady Visual Studio. Ukončení aplikace a **1** se vrátí v **okamžité** okna. Ujistěte se, že jste stále v režimu návrhu.  
   
1. Typ `?MyFunction` v **okamžité** znovu okno a stiskněte klávesu **Enter**. Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **2**. 
   
1. Nevybírejte **pokračovat**, typ `?MySub()` v **okamžité** okno a poté stiskněte klávesu **Enter**. Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **3**. Když je aplikace v režimu pozastavení můžete zkoumat stav aplikace. 
   
1. Vyberte **pokračovat**. Zarážka je dosaženo znovu a hodnota **MáFunkce** v **lokální** je okno **2**. **Okamžité** vrátí okno **výraz byl vyhodnocen a nemá žádnou hodnotu**.
   
1. Vyberte **pokračovat** znovu. Ukončení aplikace a **2** se vrátí v **okamžité** okna. Ujistěte se, že jste stále v režimu návrhu.
   
1. Vymazat obsah **okamžité** okna, klikněte pravým tlačítkem a vyberte **Vymazat vše**. 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Připojit k aplikaci z Návrháře XAML

V některých scénářích vazby deklarativní data může pomoct k ladění kódu na pozadí v Návrháři XAML.

1. V projektu sady Visual Studio, přidejte novou stránku XAML, jako například *temp.xaml*. Nová stránka XAML nechte prázdné. 
   
1. Sestavte řešení.
   
1. Otevřít *temp.xaml*, což způsobí načtení návrháře XAML *XDesProc.exe*, nebo *UwpSurface.exe* v aplikaci UWP. 
   
1. Otevřete novou instanci sady Visual Studio. V nové instanci vyberte **ladění** > **připojit k procesu**. 
   
1. V **připojit k procesu** dialogovém okně Návrhář zpracovat od **procesy k dispozici** seznamu.
   
   Pro UPW cílení na Windows sestavení 16299 nebo novější, je proces návrháře *UwpSurface.exe*. Pro WPF nebo UWP verzím 16299, proces návrháře je *XDesProc.exe*.
   
1. Ujistěte se, že **připojit k** je nastaveno na typ správný kód pro vaši verzi .NET, jako například **spravovaného kódu (CoreCLR)**. 
   
1. Vyberte **připojit**.
   
1. Zatímco připojen k procesu, přepněte na jiné instanci sady Visual Studio a nastavit zarážky, ve kterém chcete ladit kód vaší aplikace.
   
   Například můžete nastavit zarážku v kódu konvertor typu pro následující XAML, který váže objektech TextBlock v době návrhu.
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Když se stránka načte, zarážka se projeví.
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)

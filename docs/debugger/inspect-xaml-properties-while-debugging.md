---
title: Kontrola vlastností XAML při ladění | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: fcb2877a79afc310985102972d870caae560b393
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480212"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Kontrola vlastností XAML při ladění
Můžete získat v reálném čase zobrazení spuštěného kódu XAML s **dynamickém vizuálním stromu** a **Live Explorer vlastnost**. Tyto nástroje získáte stromové zobrazení prvků uživatelského rozhraní spuštěné aplikace XAML a můžete zobrazit vlastnosti runtime libovolný element uživatelského rozhraní, které vyberete.  
  
 Tyto nástroje můžete použít v následujících konfigurací:  
  
|Typ aplikace|Operačního systému a nástroje|  
|-----------------|--------------------------------|  
|Aplikace Windows Presentation Foundation (4.0 a vyšší)|Windows 7 a vyšší|  
|Univerzální aplikace pro Windows|Windows 10 a vyšší, s [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Prohlížení elementy v za provozu vizuálním stromu  
 Můžeme začít pracovat s velmi jednoduchou aplikaci WPF, která má zobrazení seznamu a tlačítko. Pokaždé, když kliknete na tlačítko, jiná položka byla přidána do seznamu. Číslované položky, se zobrazí šedě a lichých položky se žlutou.  
  
 Vytvoření nové aplikace WPF C# (Soubor > Nový > projekt, pak vyberte C# a najít aplikaci WPF). Pojmenujte ji **TestXAML**.  
  
 Změňte MainWindow.xaml následujícím způsobem:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Přidejte následující obslužná rutina příkazu do souboru MainWindow.xaml.cs:  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Sestavte projekt a spusťte ladění. (Je konfigurace sestavení musí být ladění, není verze. Další informace o konfiguracích sestavení najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).)  
  
 Až okno se zobrazí, klikněte na tlačítko **přidat položku** tlačítko několika časy. Měli byste vidět zhruba takhle:  
  
 ![Hlavní okno aplikace](../debugger/media/livevisualtree-app.png "LiveVIsualTree aplikace")  
  
 Nyní otevřete **dynamickém vizuálním stromu** okno (**ladění > Windows > dynamickém vizuálním stromu**, nebo ji najít na levé straně rozhraní IDE). Přetažením od jeho pozici ukotvení, se podíváme na toto okno a **Live vlastnosti** okna vedle sebe. V **dynamickém vizuálním stromu** okno, rozbalte **ContentPresenter** uzlu. Měl by obsahovat uzlů pro tlačítko a pole se seznamem. Rozbalte pole se seznamem (a potom **ScrollContentPresenter** a **ItemsPresenter**) k nalezení seznamu položky pole. Okno by měl vypadat takto:  
  
 ![Položky ListBoxItem v za provozu vizuálním stromu](../debugger/media/livevisualtree-listboxitems.png "položky LiveVisualTree ListBoxItem")  
  
 Přejděte zpět do okna aplikace a přidat pár další položky. Měli byste vidět další pole položky seznamu se zobrazí v **dynamickém vizuálním stromu**.  
  
 Nyní Podíváme se na vlastnosti jednoho pole položek seznamu. Vyberte první položku seznamu v **dynamickém vizuálním stromu** a klikněte na **zobrazit vlastnosti** ikonu na panelu nástrojů. **Live Explorer vlastnost** by se měla objevit. Všimněte si, že **obsahu** pole je "Item1" a **pozadí** pole je **#FFFFFFE0** (světle žlutý). Přejděte zpět **dynamickém vizuálním stromu** a vyberte druhou položku seznamu. **Live Explorer vlastnost** by měl zobrazit, který **obsahu** pole je "Item2" a **pozadí** pole je **#FFD3D3D3** (světla šedá ).  
  
 Skutečné strukturu XAML obsahuje mnoho prvky, které vás zajímají pravděpodobně není přímo, a pokud nevíte, kód a může být pevný čas přechodu stromu najít, co hledáte. Proto **dynamickém vizuálním stromu** má několika způsoby, ve kterých pomocí uživatelského rozhraní aplikace můžete najít element, které chcete prověřit.  
  
 **Povolit výběr v běžící aplikaci**. Tento režim můžete povolit, pokud klepnete na tlačítko nejvíce vlevo **dynamickém vizuálním stromu** panelu nástrojů. V tomto režimu, vám umožní vybrat prvek uživatelského rozhraní v aplikaci a **dynamickém vizuálním stromu** (a **Live prohlížeč vlastnost**) automaticky aktualizuje zobrazíte uzel ve stromu odpovídající daný element a jeho vlastnosti.  
  
 **Zobrazit ozdobného prvku rozložení v běžící aplikaci**. Tento režim můžete povolit, pokud vyberete tlačítka, které je okamžitě pravé tlačítko výběru povolit. Když **zobrazit ozdobného prvku rozložení** zapnutý, způsobí, že okno aplikace a zobrazit čáry vodorovného a svislého podél hranice vybraný objekt, abyste viděli, co ji zarovnává, a také obdélníky znázorňující pravého okraje. Například zapnout obě **umožňující výběr** a **rozložení zobrazení** on a vyberte možnost **přidat položku** blok textu v aplikaci. Byste měli vidět v uzlu bloku textu **dynamickém vizuálním stromu** a text blokování vlastnosti **Live prohlížeč vlastnost**, a také čáry vodorovného a svislého na rozsah bloku textu.  
  
 ![LivePropertyViewer v DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Náhled výběr**. Tento režim můžete povolit výběrem třetí tlačítko zleva na panelu nástrojů v dynamickém vizuálním stromu. Tento režim zobrazuje XAML, kde byla deklarována elementu, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte **umožňující výběr** a **náhled výběr**, a pak klikněte na tlačítko v naší aplikaci test. MainWindow.xaml soubor se otevře v sadě Visual Studio a kurzor je umístěn na řádku, kde je definován na tlačítko.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Pomocí nástroje XAML pro spouštění aplikací  
 Tyto nástroje XAML můžete použít i v případě, že nemáte zdrojového kódu. Když připojíte k spuštěné aplikace XAML, můžete **dynamickém vizuálním stromu** s prvky uživatelského rozhraní tuto aplikaci příliš. Tady je příklad pomocí stejné WPF testovací aplikace, které jsme nepoužili.  
  
1.  Spuštění **TestXaml** aplikace v rámci konfigurace verze. Nelze připojit k procesu, který je spuštěn v **ladění** konfigurace.  
  
2.  Otevřít druhou instanci sady Visual Studio a klikněte na tlačítko **ladění > připojit k procesu**. Najít **TestXaml.exe** v seznamu dostupných procesy a klikněte na tlačítko **Attach**.  
  
3.  Spuštění aplikace spuštěna.  
  
4.  V druhé instanci sady Visual Studio, otevřete **dynamickém vizuálním stromu** (**ladění > Windows > dynamickém vizuálním stromu**). Měli byste vidět **TestXaml** prvky uživatelského rozhraní a vy byste měli mít s nimi manipulovat, protože při ladění aplikace přímo.
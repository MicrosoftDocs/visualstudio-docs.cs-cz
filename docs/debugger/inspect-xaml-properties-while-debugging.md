---
title: Kontrolovat vlastnosti XAML při ladění | Microsoft Docs
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: fdb973718e56279e7bfb04c9d412bcd83410223d
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987752"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Kontrola vlastností XAML při ladění
Můžete získat přehled o běhu kódu XAML v reálném čase pomocí **živého vizuálního stromu** a nástroje **Live Property Explorer**. Tyto nástroje poskytují stromové zobrazení prvků uživatelského rozhraní vaší běžící aplikace XAML a zobrazují vlastnosti modulu runtime libovolného prvku uživatelského rozhraní, který vyberete.

Tyto nástroje můžete použít v následujících konfiguracích:

|Typ aplikace|Operační systém a nástroje|
|-----------------|--------------------------------|
|Aplikace Windows Presentation Foundation (4,0 a novější)|Windows 7 a novější|
|Univerzální aplikace pro Windows|Windows 10 a novější s [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|

## <a name="looking-at-elements-in-the-live-visual-tree"></a>Prohlížení prvků v živém vizuálním stromu
Pojďme začít s velmi jednoduchou aplikací WPF, která má zobrazení seznamu a tlačítko. Pokaždé, když kliknete na tlačítko, přidá se do seznamu další položka. Sudé položky jsou barevné šedé a liché položky se žlutě číslují.

Vytvořte novou C# aplikaci WPF (soubor > Nový > projekt a pak vyberte C# a vyhledejte aplikaci WPF). Pojmenujte ho **TestXAML**.

Změňte MainWindow. XAML na následující:

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

Do souboru MainWindow.xaml.cs přidejte následující obslužnou rutinu příkazu:

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

Sestavte projekt a spusťte ladění. (Konfigurace sestavení musí být ladit, nikoli vydaná verze. Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).)

Až se okno objeví, klikněte několikrát na tlačítko **Přidat položku** . Mělo by se zobrazit něco podobného:

![Hlavní okno aplikace](../debugger/media/livevisualtree-app.png "LiveVIsualTree – aplikace")

Nyní otevřete okno **živého vizuálního stromu** (**ladění > Windows > živého vizuálního stromu**nebo ho Najděte na levé straně rozhraní IDE). Přetáhněte ho z jeho dokovací pozice, abychom se mohli podívat na toto okno a okno **živé vlastnosti** vedle sebe. V okně **živé vizuální stromové struktury** rozbalte uzel **ContentPresenter** . Měl by obsahovat uzly pro tlačítko a pole se seznamem. Rozbalte seznam (a pak **ScrollContentPresenter** a **ItemsPresenter**) a vyhledejte položky seznamu. Okno by mělo vypadat takto:

![ListBoxItems ve živém vizuálním stromu](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree – ListBoxItems")

Vraťte se do okna aplikace a přidejte několik dalších položek. V **živém vizuálním stromu**by se měla zobrazit více položek v poli se seznamem.

Nyní se podívejme na vlastnosti jedné z položek seznamu. Vyberte první položku seznamu v **živém vizuálním stromu** a na panelu nástrojů klikněte na ikonu **Zobrazit vlastnosti** . Měl by se zobrazit **Průzkumník vlastností živě** . Všimněte si, že pole **Content** je "Item1 –" a pole na **pozadí** je **#FFFFFFE0** (světle žlutá). Vraťte se do **živého vizuálního stromu** a vyberte položku se seznamem sekund. V nástroji **Live Property Explorer** by se měl zobrazit, že pole **Content** je "Item2" a pole na **pozadí** je **#FFD3D3D3** (světle šedá).

Skutečná struktura XAML má velký počet prvků, na které se pravděpodobně nepřímo zajímáte, a pokud neznáte kód, může se stát, že budete mít k dispozici nějaký tvrdý čas navigace ve stromu, aby bylo možné najít, co hledáte. Proto má **živý vizuální strom** několik způsobů, jak můžete použít uživatelské rozhraní aplikace, které vám pomůžou najít prvek, který chcete prošetřit.

**Povolí výběr v běžící aplikaci**. Tento režim můžete povolit po výběru tlačítka úplně vlevo na panelu nástrojů **živého vizuálního stromu** . V tomto režimu můžete vybrat prvek uživatelského rozhraní v aplikaci a **živý vizuální strom** (a **živý prohlížeč vlastností**) se automaticky aktualizuje, aby zobrazil uzel ve stromu odpovídající tomuto prvku a jeho vlastnosti.

**Zobrazit doplňky pro úpravy rozložení v běžící aplikaci**. Tento režim můžete povolit, když vyberete tlačítko, které je okamžitě napravo od tlačítka povolit výběr. Když je doplněk **zobrazení rozložení** zapnutý, způsobí, že okno aplikace zobrazí vodorovnou a svislou spojnici podél hranic vybraného objektu, abyste viděli, k čemu se zarovnává, a také obdélníky znázorňující okraje. Můžete například zapnout možnost **Povolit výběr** i **rozložení zobrazení** a v aplikaci vybrat blok textu **Přidat položku** . Měli byste vidět uzel blok textu v **živém vizuálním stromu** a vlastnosti bloku textu v **nástroji Live Property Viewer**a také vodorovné a svislé čáry na hranicích textového bloku.

![LivePropertyViewer v DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer – DisplayLayout")

**Náhled výběru**. Tento režim můžete povolit tak, že vyberete třetí tlačítko vlevo na panelu nástrojů živého vizuálního stromu. Tento režim zobrazuje kód XAML, kde byl element deklarován, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte možnost **Povolit výběr** a **Náhled výběru**a potom vyberte tlačítko v naší testovací aplikaci. Otevře se soubor MainWindow. XAML v aplikaci Visual Studio a kurzor je umístěn na řádku, kde je tlačítko definováno.

## <a name="using-xaml-tools-with-running-applications"></a>Používání nástrojů XAML se spuštěnými aplikacemi
Tyto nástroje XAML můžete použít i v případě, že nemáte zdrojový kód. Když se připojíte ke spuštěné aplikaci XAML, můžete použít také **živý vizuální strom** na prvcích uživatelského rozhraní této aplikace. Tady je příklad pomocí stejné testovací aplikace WPF, kterou jsme použili dřív.

1. V konfiguraci vydané verze spusťte aplikaci **TestXaml** . Nemůžete se připojit k procesu, který je spuštěný v konfiguraci **ladění** .

2. Otevřete druhou instanci aplikace Visual Studio a klikněte na položku **ladit > připojit k procesu**. V seznamu dostupných procesů vyhledejte **TestXaml. exe** a klikněte na **připojit**.

3. Aplikace začne běžet.

4. Ve druhé instanci aplikace Visual Studio otevřete **živý vizuální strom** (**ladění > Windows > Live Visual Tree**). Měli byste vidět prvky uživatelského rozhraní **TestXaml** a měli byste být schopni je manipulovat stejně jako při přímém ladění aplikace.

## <a name="see-also"></a>Viz také:

[Zápis a ladění spuštěného kódu XAML pomocí horkého opětovného načtení XAML](xaml-hot-reload.md)

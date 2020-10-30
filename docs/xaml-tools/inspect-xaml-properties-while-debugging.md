---
title: Kontrolovat vlastnosti XAML při ladění | Microsoft Docs
description: Naučte se používat živý vizuální strom a nástroje Průzkumníka živých vlastností při ladění pro kontrolu vlastností XAML a získání stromového zobrazení prvků uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 11/12/2019
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 5fb3c1fff831fdee711340345c283dbeaf3f13a6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046073"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Kontrola vlastností XAML při ladění

Můžete získat přehled o běhu kódu XAML v reálném čase pomocí **živého vizuálního stromu** a nástroje **Live Property Explorer** . Tyto nástroje poskytují stromové zobrazení prvků uživatelského rozhraní vaší běžící aplikace XAML a zobrazují vlastnosti modulu runtime libovolného prvku uživatelského rozhraní, který vyberete.

Tyto nástroje můžete použít v následujících konfiguracích:

|Typ aplikace|Operační systém a nástroje|
|-----------------|--------------------------------|
|Aplikace Windows Presentation Foundation (4,0 a novější)|Windows 7 a novější|
|Univerzální aplikace pro Windows|Windows 10 a novější s [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Podívejte se na prvky v živém vizuálním stromu.

Pojďme začít s velmi jednoduchou aplikací WPF, která má zobrazení seznamu a tlačítko. Pokaždé, když kliknete na tlačítko, přidá se do seznamu další položka. Sudé položky jsou barevné šedé a liché položky se žlutě číslují.

### <a name="create-the-project"></a>Vytvoření projektu

1. Vytvořte novou aplikaci WPF v jazyce c# ( **soubor**  >  **Nový**  >  **projekt** , zadejte "c# WPF" a zvolte buď **aplikaci WPF (.NET Core)** nebo **aplikaci WPF (.NET Framework)** ). Pojmenujte ho **TestXAML** .

1. Změňte MainWindow. XAML na následující:

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

1. Do souboru MainWindow.xaml.cs přidejte následující obslužnou rutinu příkazu:

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

1. Sestavte projekt a spusťte ladění. (Konfigurace sestavení musí být ladit, nikoli vydaná verze. Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).)

   Po zobrazení okna byste měli vidět, že se ve spuštěné aplikaci zobrazí panel nástrojů ve vaší aplikaci.

   ::: moniker range=">= vs-2019"
   ![Hlavní okno aplikace](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Hlavní okno aplikace](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Nyní kliknutím na tlačítko **Přidat položku** několikrát přidejte nové položky do seznamu.

### <a name="inspect-xaml-properties"></a>Vlastnosti jazyka XAML

1. V dalším kroku otevřete okno **živého vizuálního stromu** kliknutím na tlačítko zcela vlevo na panelu nástrojů v aplikaci (nebo v části **ladění > Windows > živý vizuální strom** ). Po jeho otevření ho přetáhněte z jeho dokovací pozice, abychom se mohli podívat na toto okno a okno **živé vlastnosti** vedle sebe.

1. V okně **živé vizuální stromové struktury** rozbalte uzel **ContentPresenter** . Měl by obsahovat uzly pro tlačítko a pole se seznamem. Rozbalte seznam (a pak **ScrollContentPresenter** a **ItemsPresenter** ) a vyhledejte položky seznamu.

   ::: moniker range=">= vs-2019"
   Pokud nevidíte uzel **ContentPresenter** , na panelu nástrojů přepněte ikonu **Zobrazit pouze můj kód XAML** . Počínaje verzí Visual Studio 2019 verze 16,4 je zobrazení prvků XAML zjednodušeno ve výchozím nastavení pomocí funkce pouze můj kód XAML. [Toto nastavení](../debugger/general-debugging-options-dialog-box.md) můžete také zakázat v možnosti, chcete-li vždy zobrazit všechny prvky XAML.
   ::: moniker-end

   Okno by mělo vypadat takto:

   ::: moniker range=">= vs-2019"
   ![ListBoxItems ve živém vizuálním stromu](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![ListBoxItems ve živém vizuálním stromu](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Vraťte se do okna aplikace a přidejte několik dalších položek. V **živém vizuálním stromu** by se měla zobrazit více položek v poli se seznamem.

1. Nyní se podívejme na vlastnosti jedné z položek seznamu.

   Vyberte první položku seznamu v **živém vizuálním stromu** a na panelu nástrojů klikněte na ikonu **Zobrazit vlastnosti** . Měl by se zobrazit **Průzkumník vlastností živě** . Všimněte si, že pole **Content** je "Item1 –" a pole **Background**  >  **Barva** pozadí je **#FFFFFFE0** .

1. Vraťte se do **živého vizuálního stromu** a vyberte položku se seznamem sekund. V nástroji **Live Property Explorer** by se měl zobrazit, že pole **Content** je "Item2" a **Background**  >  **pole Barva** pozadí je **#FFD3D3D3** (v závislosti na motivu).

   > [!NOTE]
   > Žluté ohraničení kolem vlastnosti v nástroji **Live Property Explorer** znamená, že hodnota vlastnosti je nastavena prostřednictvím vazby, například `Color = {BindingExpression}` . Zelená ohraničení znamená, že hodnota je nastavena pomocí prostředku, například `Color = {StaticResource MyBrush}` .

   Skutečná struktura XAML má velký počet prvků, na které se pravděpodobně nepřímo zajímáte, a pokud neznáte kód, může se stát, že budete mít k dispozici nějaký tvrdý čas navigace ve stromu, aby bylo možné najít, co hledáte. Proto má **živý vizuální strom** několik způsobů, jak můžete použít uživatelské rozhraní aplikace, které vám pomůžou najít prvek, který chcete prošetřit.

   ::: moniker range=">= vs-2019"
   **Vyberte element v běžící aplikaci** . Tento režim můžete povolit po výběru tlačítka úplně vlevo na panelu nástrojů **živého vizuálního stromu** . V tomto režimu můžete vybrat prvek uživatelského rozhraní v aplikaci a **živý vizuální strom** (a **živý prohlížeč vlastností** ) se automaticky aktualizuje, aby zobrazil uzel ve stromu odpovídající tomuto prvku a jeho vlastnosti. Počínaje verzí Visual Studio 2019 verze 16,4 můžete [nakonfigurovat chování výběru prvků](../debugger/general-debugging-options-dialog-box.md).

   **Zobrazit doplňky pro úpravy rozložení v běžící aplikaci** . Tento režim můžete povolit, když vyberete tlačítko, které je okamžitě napravo od tlačítka povolit výběr. Když je doplněk **zobrazení rozložení** zapnutý, způsobí, že okno aplikace zobrazí vodorovnou a svislou spojnici podél hranic vybraného objektu, abyste viděli, k čemu se zarovnává, a také obdélníky znázorňující okraje. Můžete například zapnout jak **Výběr elementu** , tak **zobrazení rozložení** , a v aplikaci vybrat blok textu **Přidat položku** . Měli byste vidět uzel blok textu v **živém vizuálním stromu** a vlastnosti bloku textu v **nástroji Live Property Viewer** a také vodorovné a svislé čáry na hranicích textového bloku.

   ![LivePropertyViewer v DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Náhled výběru** . Tento režim můžete povolit tak, že vyberete třetí tlačítko vlevo na panelu nástrojů živého vizuálního stromu. Tento režim zobrazuje kód XAML, kde byl element deklarován, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte **Vybrat prvek** a **Náhled výběru** a potom vyberte tlačítko v naší testovací aplikaci. Otevře se soubor MainWindow. XAML v aplikaci Visual Studio a kurzor je umístěn na řádku, kde je tlačítko definováno.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Povolí výběr v běžící aplikaci** . Tento režim můžete povolit po výběru tlačítka úplně vlevo na panelu nástrojů **živého vizuálního stromu** . V tomto režimu můžete vybrat prvek uživatelského rozhraní v aplikaci a **živý vizuální strom** (a **živý prohlížeč vlastností** ) se automaticky aktualizuje, aby zobrazil uzel ve stromu odpovídající tomuto prvku a jeho vlastnosti.

   **Zobrazit doplňky pro úpravy rozložení v běžící aplikaci** . Tento režim můžete povolit, když vyberete tlačítko, které je okamžitě napravo od tlačítka povolit výběr. Když je doplněk **zobrazení rozložení** zapnutý, způsobí, že okno aplikace zobrazí vodorovnou a svislou spojnici podél hranic vybraného objektu, abyste viděli, k čemu se zarovnává, a také obdélníky znázorňující okraje. Můžete například zapnout možnost **Povolit výběr** i **rozložení zobrazení** a v aplikaci vybrat blok textu **Přidat položku** . Měli byste vidět uzel blok textu v **živém vizuálním stromu** a vlastnosti bloku textu v **nástroji Live Property Viewer** a také vodorovné a svislé čáry na hranicích textového bloku.

   ![LivePropertyViewer v DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Náhled výběru** . Tento režim můžete povolit tak, že vyberete třetí tlačítko vlevo na panelu nástrojů živého vizuálního stromu. Tento režim zobrazuje kód XAML, kde byl element deklarován, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte možnost **Povolit výběr** a **Náhled výběru** a potom vyberte tlačítko v naší testovací aplikaci. Otevře se soubor MainWindow. XAML v aplikaci Visual Studio a kurzor je umístěn na řádku, kde je tlačítko definováno.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Použití nástrojů XAML se spuštěnými aplikacemi

Tyto nástroje XAML můžete použít i v případě, že nemáte zdrojový kód. Když se připojíte ke spuštěné aplikaci XAML, můžete použít také **živý vizuální strom** na prvcích uživatelského rozhraní této aplikace. Tady je příklad pomocí stejné testovací aplikace WPF, kterou jsme použili dřív.

1. V konfiguraci vydané verze spusťte aplikaci **TestXaml** . Nemůžete se připojit k procesu, který je spuštěný v konfiguraci **ladění** .

2. Otevřete druhou instanci aplikace Visual Studio a klikněte na položku **ladit > připojit k procesu** . V seznamu dostupných procesů vyhledejte **TestXaml.exe** a klikněte na **připojit** .

3. Aplikace začne běžet.

4. Ve druhé instanci aplikace Visual Studio otevřete **živý vizuální strom** ( **ladění > Windows > Live Visual Tree** ). Měli byste vidět prvky uživatelského rozhraní **TestXaml** a měli byste být schopni je manipulovat stejně jako při přímém ladění aplikace.

## <a name="see-also"></a>Viz také

[Zápis a ladění spuštěného kódu XAML pomocí horkého opětovného načtení XAML](xaml-hot-reload.md)

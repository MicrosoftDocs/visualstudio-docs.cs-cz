---
title: Kontrola vlastností XAML při ladění | Microsoft Docs
description: Naučte se používat živé vizuální stromy a nástroje Live Property Explorer při ladění ke kontrole vlastností XAML a získání stromového zobrazení prvků uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 86310346566e8c937c2769a9fcc9f0d4e98b3ae2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308438"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Kontrola vlastností XAML při ladění

Zobrazení spuštěného kódu XAML v reálném čase  můžete získat pomocí živého vizuálního stromu a živého **Průzkumníka vlastností**. Tyto nástroje poskytují stromové zobrazení prvků uživatelského rozhraní spuštěné aplikace XAML a zobrazují vlastnosti modulu runtime libovolného prvku uživatelského rozhraní, který vyberete.

Tyto nástroje můžete použít v následujících konfiguracích:

|Typ aplikace|Operační systém a nástroje|
|-----------------|--------------------------------|
|Windows Presentation Foundation (4.0 a vyšší)|Windows 7 a vyšší|
|Univerzální aplikace pro Windows|Windows 10 a vyšší s Windows 10 [SDK](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Prohlédněte si elementy v živém vizuálním stromu.

Začme s velmi jednoduchou aplikací WPF, která má zobrazení seznamu a tlačítko. Pokaždé, když na tlačítko kliknete, se do seznamu přidá další položka. Položky s sudými čísly jsou barevné šedé a liché položky mají žlutou barvu.

### <a name="create-the-project"></a>Vytvoření projektu

::: moniker range=">=vs-2019"

1. Vytvořte novou aplikaci WPF C#**(** Soubor nový projekt, zadejte "C# WPF", zvolte šablonu projektu aplikace WPF, pojmerujte projekt TestXAML a ověřte, že se v rozevíracím seznamu Cílová rozhraní zobrazuje >  >  **.NET Core 3.1.**   

::: moniker-end

::: moniker range="vs-2017"

1. Vytvořte novou aplikaci WPF C# (**Soubor**  >  **nový**  >  projekt, zadejte "C# WPF" a zvolte **WPF App (.NET Framework)**). Pojmnujte **ji TestXAML**.

::: moniker-end

1. Změňte MainWindow.xaml na následující:

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

1. Sestavte projekt a spusťte ladění. (Konfigurace sestavení musí být Debug(Ladění), nikoli Release (Vypustit). Další informace o konfiguracích sestavení najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).)

   Po zobrazení okna by se měl v běžící aplikaci zobrazit panel nástrojů v aplikaci.

   ::: moniker range=">= vs-2019"
   ![Hlavní okno aplikace](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Hlavní okno aplikace](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Teď několikrát klikněte **na tlačítko Přidat** položku a přidejte do seznamu nové položky.

### <a name="inspect-xaml-properties"></a>Vlastnosti jazyka XAML

1. Pak kliknutím na tlačítko vlevo na panelu nástrojů v aplikaci (nebo v části Ladit > **Windows > Live Visual Tree)** otevřete okno Live **Visual** Tree. Jakmile je okno otevřené, přetáhněte ho ze své pozice ukotvení, abychom se mohli podívat na toto okno a okno Živých vlastností vedle sebe. 

1. V okně **Live Visual Tree** rozbalte uzel **ContentPresenter.** Měl by obsahovat uzly pro tlačítko a seznam. Rozbalte seznam (a pak **položky ScrollContentPresenter** a **ItemsPresenter)** a vyhledejte položky seznamu.

   ::: moniker range=">= vs-2019"
   Pokud uzel **ContentPresenter nevidíte,** přepněte na panelu nástrojů ikonu Zobrazit jenom můj **KÓD** XAML. Počínaje Visual Studio 2019 verze 16.4 je zobrazení elementů XAML ve výchozím nastavení zjednodušené pomocí funkce Jen můj KÓD XAML. Toto nastavení můžete [také zakázat v možnostech,](../debugger/general-debugging-options-dialog-box.md) aby se vždy zobrazují všechny elementy XAML.
   ::: moniker-end

   Okno by mělo vypadat takhle:

   ::: moniker range=">= vs-2019"
   ![ListBoxItems v živém vizuálním stromu](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![ListBoxItems v živém vizuálním stromu](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Zpět do okna aplikace a přidejte několik dalších položek. V živém vizuálním stromu by se měly zobrazit další **položky seznamu.**

1. Teď se podívejme na vlastnosti jedné z položek seznamu.

   Vyberte první položku seznamu v **živém** vizuálním stromu a klikněte na ikonu **Zobrazit** vlastnosti na panelu nástrojů. Měl **by se zobrazit Prohlížeč živých** vlastností. Všimněte **si, že** pole Obsah je Item1 a pole  >  **Barva pozadí** je **#FFFFFFE0**.

1. Zpět do živého **vizuálního stromu** a vyberte druhou položku seznamu. V **Prohlížeči živých**  vlastností by se mělo zobrazit, že pole Obsah je Item2 a pole Barva pozadí je #FFD3D3D3 (v závislosti   >   na  motivu).

   > [!NOTE]
   > Žluté ohraničení kolem vlastnosti v **Prohlížeči** živých vlastností znamená, že hodnota vlastnosti se nastavuje prostřednictvím vazby, například `Color = {BindingExpression}` . Zelené ohraničení znamená, že hodnota je nastavená pomocí prostředku, například `Color = {StaticResource MyBrush}` .

   Skutečná struktura XAML má spoustu prvků, které vás pravděpodobně přímo nezajímají, a pokud kód dobře nevíte, může být obtížné přejít ve stromu a najít, co hledáte. Live **Visual Tree má** několik způsobů, které vám umožňují pomocí uživatelského rozhraní aplikace najít prvek, který chcete prozkoumat.

   ::: moniker range=">= vs-2019"
   **V běžící aplikaci vyberte element**. Tento režim můžete povolit, když na panelu nástrojů Live **Visual Tree** vyberete tlačítko nejvíce vlevo. V tomto režimu můžete vybrat prvek uživatelského rozhraní v aplikaci a živý vizuální strom **(a** Prohlížeč živých vlastností) se automaticky aktualizuje tak, aby se uzel ve stromu odpovídajícím tomuto prvku a jeho vlastnostech zobrazí. Počínaje Visual Studio 2019 verze 16.4 můžete nakonfigurovat chování [výběru elementu](../debugger/general-debugging-options-dialog-box.md).

   **Doplňky pro zobrazení rozložení ve spuštěné aplikaci** Tento režim můžete povolit, když vyberete tlačítko, které je hned napravo od tlačítka Povolit výběr. Když jsou **doplňky** pro zobrazení rozložení zaškrtnuté, způsobí to, že se v okně aplikace zobrazí podél meze vybraného objektu vodorovné a svislé čáry, abyste viděli, k čemu je zarovnaný, a také obdélníky zobrazující okraje. Zapněte například element **Select** i **Rozložení zobrazení** a v aplikaci vyberte textový blok Přidat položku.  V živém vizuálním stromu  byste měli vidět uzel bloku textu a vlastnosti bloku textu v Prohlížeči živých vlastností a také vodorovné a svislé čáry na hranicích textového bloku.

   ![LivePropertyViewer v DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Náhled výběru**. Tento režim můžete povolit výběrem třetího tlačítka vlevo na panelu nástrojů Live Visual Tree. Tento režim ukazuje XAML, kde byl element deklarován, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte **Vybrat prvek a** náhled **výběru** a pak vyberte tlačítko v naší testovací aplikaci. Soubor MainWindow.xaml se otevře v Visual Studio a kurzor je umístěn na řádek, kde je tlačítko definováno.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Povolte výběr ve spuštěné aplikaci.** Tento režim můžete povolit, když na panelu nástrojů Live **Visual Tree** vyberete tlačítko nejvíce vlevo. V tomto režimu můžete vybrat prvek uživatelského rozhraní v aplikaci a živý vizuální strom **(a** Prohlížeč živých vlastností) se automaticky aktualizuje tak, aby se uzel ve stromu odpovídajícím tomuto prvku a jeho vlastnostech zobrazí.

   **Doplňky pro zobrazení rozložení ve spuštěné aplikaci** Tento režim můžete povolit, když vyberete tlačítko, které je hned napravo od tlačítka Povolit výběr. Když jsou **doplňky** pro zobrazení rozložení zaškrtnuté, způsobí to, že se v okně aplikace zobrazí podél meze vybraného objektu vodorovné a svislé čáry, abyste viděli, k čemu je zarovnaný, a také obdélníky zobrazující okraje. Zapněte například Povolit výběr **i** **Zobrazit rozložení** a vyberte v aplikaci textový **blok** Přidat položku. V živém vizuálním stromu  byste měli vidět uzel bloku textu a vlastnosti bloku textu v Prohlížeči živých vlastností a také vodorovné a svislé čáry na hranicích textového bloku.

   ![LivePropertyViewer v DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Náhled výběru**. Tento režim můžete povolit výběrem třetího tlačítka vlevo na panelu nástrojů Live Visual Tree. Tento režim ukazuje XAML, kde byl element deklarován, pokud máte přístup ke zdrojovému kódu aplikace. Vyberte **Povolit výběr a** náhled **a** pak vyberte tlačítko v naší testovací aplikaci. Soubor MainWindow.xaml se otevře v Visual Studio a kurzor je umístěn na řádek, kde je tlačítko definováno.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Použití nástrojů XAML se spouštěním aplikací

Tyto nástroje XAML můžete použít i v případě, že nemáte zdrojový kód. Když se připojíte ke spuštěné aplikaci XAML, můžete použít živý **vizuální** strom také na prvcích uživatelského rozhraní této aplikace. Tady je příklad použití stejné testovací aplikace WPF, jako jsme použili dříve.

1. V **konfiguraci vydání spusťte aplikaci TestXaml.** Nelze se připojit k procesu, který běží v **konfiguraci ladění.**

2. Otevřete druhou instanci služby Visual Studio klikněte na **Ladit a > připojit k procesu**. Vyhledejte **TestXaml.exe** seznamu dostupných procesů a klikněte na **Připojit.**

3. Aplikace se spustí.

4. Ve druhé instanci Visual Studio otevřete živý **vizuální** strom (**Ladění > Windows > Live Visual Tree**). Měli byste vidět prvky **uživatelského rozhraní TestXaml** a měli byste být schopni s nimi manipulovat stejně jako při přímém ladění aplikace.

## <a name="see-also"></a>Viz také

[Psaní a ladění spuštěného kódu XAML pomocí Opětovné načítání XAML za provozu](xaml-hot-reload.md)

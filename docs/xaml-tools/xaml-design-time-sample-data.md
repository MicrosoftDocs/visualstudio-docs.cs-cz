---
title: Použití ukázkových dat v době návrhu s Návrhář XAML v Visual Studio
description: Naučte se používat ukázková data v době návrhu v jazyce XAML.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 8303e1150db7c12c404e8f67bce52418fbd05b9d
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433789"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Použití ukázkových dat v době návrhu s Návrhář XAML v Visual Studio

Některé ovládací prvky, jako je ListView, ListBox nebo DataGrid, jsou bez dat těžko vizualizované. V tomto dokumentu se budeme seznamovat s novým přístupem, který vývojářům pracujícím na projektech **WPF .NET Core** nebo **WPF .NET Framework** umožňuje pomocí nového návrháře povolit ukázková data v těchto ovládacích prvcích. 

## <a name="sample-data-feature-basics"></a>Základní informace o funkcích ukázkových dat

Ukázková data jsou jenom pro vizualizaci v době návrhu, což znamená, že se zobrazí pouze v návrháři XAML, ne v běžící aplikaci. Proto se použije na verzi návrhu vlastnosti ItemsSource `d:ItemsSource` . Ukázková data potřebují, aby obor názvů v době návrhu fungoval. Pokud chcete začít, přidejte do hlavičky dokumentu XAML následující řádky kódu, pokud ještě nejsou k dispozici:

> [!NOTE]
> Další [informace o vlastnostech doby](../xaml-tools/xaml-designtime-data.md) návrhu v jazyce XAML najdete ve vlastnostech návrhu XAML.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Po přidání oborů názvů můžete pomocí povolit `d:ItemsSource="{d:SampleData}"` ukázková data v ListView, Listboxu nebo DataGridu. Příklad:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Ukázková data s datagridem](media\xaml-sample-data-empty-datagrid.png "Ukázková data povolená pro DataGrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

V tomto příkladu by `d:ItemsSource="{d:SampleData}"` se bez Návrhář XAML data zobrazí prázdná datová mřížka. Místo toho se `d:SampleData` teď zobrazí vygenerovaná výchozí ukázková data.

Ve výchozím nastavení se zobrazí 5 položek. Pomocí vlastnosti **ItemCount** však můžete určit, kolik položek chcete zobrazit. například: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Ukázková data fungují s datovými šablonami

Při použití šablon dat fungují ukázková data pro ovládací prvky ListBox, ListView nebo DataGrid. Funkce Ukázková data analyzuje dataTemplate a pokusí se pro něj vygenerovat příslušná data. Ukázková data se vygenerují pouze pro prvky v šablonách DataTemplates, které používají vazby. Ukázková data se vygenerují i v případě, že vazby ještě nemají zdroj.
Příklad:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Zobrazení ListView ukázkových dat s objektem DataTemplate](media\xaml-sample-data-templated-listview.png "Ukázková data použitá v objektu ListView se šablonou DataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Povolení ukázkových dat s navrhovanými akcemi

Pokud chcete v návrháři snadno povolit nebo zakázat ukázková data pro ovládací prvek, můžete použít funkci Navrhované akce. Suggested Actions (Navrhované akce) je žárovka v návrháři, která se zobrazí v pravém horním rohu při výběru ovládacího prvku. Ukázková data můžete povolit tak, že vyberete ovládací prvek, kliknete na žárovku a pak kliknete na `Show Sample Data` . Příklad:

[![Ukázkové akce navrhované daty](media\xaml-sample-data-suggested-actions.png "Povolení ukázkových dat s navrhovanými akcemi")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Ukázková data s IValueConverters 

Funkce Ukázková data převaděče plně nepodporuje. Můžete ho ale zpracuje jedním nebo oběma z následujících způsobů:
- Ujistěte se, `Convert` že vaše funkce dokáže zpracovat scénář, ve kterém už je hodnota targetType.

- Implementujte `ConvertBack` funkci , která převede vaši hodnotu zpět na původní typ. 

## <a name="troubleshooting"></a>Řešení potíží

Pokud se v ukázkových datech nic nezobrazuje nebo se vám nepodaří zobrazit správný typ, můžete zkusit aktualizovat návrháře nebo stránku zavřít a znovu otevřít.

Pokud nastane problém, který není v této části uvedený, nebo ho nejde vyřešit aktualizací stránky, dejte nám vědět pomocí nástroje [pro](../ide/how-to-report-a-problem-with-visual-studio.md) nahlášení problému.

### <a name="requirements"></a>Požadavky

- Ukázková data vyžadují Visual Studio 2019 [verze 16.10](/visualstudio/releases/2019/release-notes-v16.10) nebo novější.

- Podporuje desktopové projekty Windows, které jsou Windows Presentation Foundation (WPF) pro .NET Core nebo .NET Framework při použití nového návrháře. Pokud chcete povolit nového návrháře pro .NET Framework přejděte na Nástroje > Možnosti > Prostředí > Funkce preview, vyberte Nový WPF Návrhář XAML pro .NET Framework a pak restartujte Visual Studio.

## <a name="see-also"></a>Viz také

- [Vlastnosti návrhu XAML](../xaml-tools/xaml-designtime-data.md)
- [XAML v aplikacích WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML v aplikacích pro UPW](/windows/uwp/xaml-platform/xaml-overview)
- [XAML v aplikacích Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
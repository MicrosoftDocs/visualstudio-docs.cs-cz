---
title: Vytvoření ovládacího prvku panelu nástrojů WPF | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa6051648e495e21f7954a737f7b572ce6a6f2
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903949"
---
# <a name="create-a-wpf-toolbox-control"></a>Vytvoření ovládacího prvku sady nástrojů WPF

Šablona ovládacího prvku panelu nástrojů WPF (Windows Presentation Framework) umožňuje vytvořit ovládací prvky WPF, které jsou automaticky přidány do **sady nástrojů** při instalaci rozšíření. Tento návod ukazuje, jak použít šablonu k vytvoření ovládacího prvku **sady nástrojů** , který můžete distribuovat dalším uživatelům.

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Vytvoření rozšíření pomocí ovládacího prvku sady nástrojů WPF

1. Vytvořte projekt VSIX s názvem `MyToolboxControl` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Po otevření projektu přidejte šablonu položky **ovládacího prvku sady nástrojů WPF** s názvem `MyToolboxControl` . V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** přejdete na rozšiřitelnost v jazyce **Visual C#**  >  **Extensibility** a vyberete **ovládací prvek sada nástrojů WPF**. V poli **název** v dolní části okna změňte název souboru příkazů na *MyToolboxControl.cs*.

    Řešení nyní obsahuje uživatelský ovládací prvek, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> který přidá ovládací prvek do **panelu nástrojů**a položku prostředku **Microsoft. VISUALSTUDIO. ToolboxControl** v manifestu VSIX pro nasazení.

#### <a name="to-create-the-control-ui"></a>Vytvoření uživatelského rozhraní ovládacího prvku

1. Otevřete *MyToolboxControl. XAML* v návrháři.

    Návrhář zobrazí <xref:System.Windows.Controls.Grid> ovládací prvek, který obsahuje <xref:System.Windows.Controls.Button> ovládací prvek.

2. Uspořádat rozložení mřížky Když vyberete <xref:System.Windows.Controls.Grid> ovládací prvek, v horním a levém okraji mřížky se zobrazí modré ovládací panely. Řádky a sloupce můžete do mřížky přidat kliknutím na pruhy.

3. Přidejte do mřížky podřízené ovládací prvky. Podřízený ovládací prvek lze umístit přetažením ze **sady nástrojů** do části mřížky nebo nastavením jeho `Grid.Row` `Grid.Column` atributů a v jazyce XAML. Následující příklad přidá dva popisky na horní řádek mřížky a tlačítko na druhý řádek.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Přejmenování ovládacího prvku

 Ve výchozím nastavení se ovládací prvek zobrazí v sadě **nástrojů** jako **MyToolboxControl** ve skupině s názvem **MyToolboxControl. MyToolboxControl**. Tyto názvy můžete změnit v souboru *MyToolboxControl.XAML.cs* .

1. Otevřete *MyToolboxControl.XAML.cs* v zobrazení kódu.

2. Najděte `MyToolboxControl` třídu a přejmenujte ji na TestControl. (Nejrychlejší způsob, jak to provést, je přejmenovat třídu a pak vybrat **Přejmenovat** z kontextové nabídky a dokončit kroky. (Další informace o příkazu **Přejmenovat** naleznete v tématu [refaktoringu přejmenování (C#)](../ide/reference/rename.md).)

3. Přejděte na `ProvideToolboxControl` atribut a změňte hodnotu prvního parametru na **test**. Toto je název skupiny, která bude obsahovat ovládací prvek v sadě **nástrojů**.

    Výsledný kód by měl vypadat takto:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Sestavování, testování a nasazování

 Při ladění projektu byste měli najít ovládací prvek nainstalovaný v **sadě nástrojů** experimentální instance sady Visual Studio.

### <a name="to-build-and-test-the-control"></a>Sestavení a otestování ovládacího prvku

1. Znovu sestavte projekt a spusťte ladění.

2. V nové instanci sady Visual Studio vytvořte projekt aplikace WPF. Ujistěte se, že je Návrhář XAML otevřeno.

3. Vyhledejte ovládací prvek v **sadě nástrojů** a přetáhněte jej na návrhovou plochu.

4. Spusťte ladění aplikace WPF.

5. Ověřte, zda se ovládací prvek zobrazuje.

### <a name="to-deploy-the-control"></a>Nasazení ovládacího prvku

1. Po sestavení testovaného projektu můžete najít soubor *. vsix* ve složce * \bin\debug \* projektu.

2. Můžete ji nainstalovat na místní počítač dvojitým kliknutím na soubor *. vsix* a podle postupu instalace. Chcete-li odinstalovat ovládací prvek, přejděte do části **nástroje**  >  **rozšíření a aktualizace** a vyhledejte rozšíření ovládacího prvku a pak klikněte na možnost **odinstalovat**.

3. Nahrajte soubor *. vsix* do sítě nebo na web.

    Pokud soubor nahrajete na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) web, jiní uživatelé mohou pomocí rozšíření **nástrojů**  >  **a aktualizací** v aplikaci Visual Studio najít kontrolu online a nainstalovat ji.

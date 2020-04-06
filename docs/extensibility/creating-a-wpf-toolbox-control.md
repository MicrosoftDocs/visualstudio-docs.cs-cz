---
title: Vytvoření ovládacího prvku WPF Toolbox | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739564"
---
# <a name="create-a-wpf-toolbox-control"></a>Vytvoření ovládacího prvku WPF Toolbox

Šablona Ovládací prvek panelu nástrojů WPF (Windows Presentation Framework) umožňuje vytvářet ovládací prvky WPF, které jsou automaticky přidány do **panelu nástrojů** při instalaci rozšíření. Tento návod ukazuje, jak pomocí šablony vytvořit ovládací prvek **panelu nástrojů,** který můžete distribuovat ostatním uživatelům.

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Vytvoření ovládacího prvku Panelu nástrojů

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Vytvoření rozšíření pomocí ovládacího prvku WPF Toolbox

1. Vytvořte projekt VSIX s názvem `MyToolboxControl`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Po otevření projektu přidejte šablonu **položky ovládacího prvku WPF Toolbox** s názvem `MyToolboxControl`. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **ovládací prvek panelu nástrojů WPF**. V poli **Název** v dolní části okna změňte název příkazového souboru na *MyToolboxControl.cs*.

    Řešení nyní obsahuje uživatelský ovládací `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> prvek, a který přidá ovládací prvek do **panelu nástrojů**a **položku Microsoft.VisualStudio.ToolboxControl** asset v manifestu VSIX pro nasazení.

#### <a name="to-create-the-control-ui"></a>Vytvoření ovládacího prvku

1. Otevřete *mytoolboxControl.xaml* v návrháři.

    Návrhář zobrazí <xref:System.Windows.Controls.Grid> ovládací prvek, <xref:System.Windows.Controls.Button> který obsahuje ovládací prvek.

2. Uspořádejte rozložení mřížky. Když vyberete <xref:System.Windows.Controls.Grid> ovládací prvek, modré ovládací pruhy se zobrazí na horním a levém okraji mřížky. Řádky a sloupce můžete do mřížky přidat kliknutím na pruhy.

3. Přidejte podřízené ovládací prvky do mřížky. Podřízený ovládací prvek můžete umístit přetažením z **panelu nástrojů** do části `Grid.Row` `Grid.Column` mřížky nebo nastavením jeho atributů a atributů v xaml. Následující příklad přidá dva popisky na horním řádku mřížky a tlačítko na druhém řádku.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Přejmenování ovládacího prvku

 Ve výchozím nastavení se ovládací prvek zobrazí v **panelu nástrojů** jako **MyToolboxControl** ve skupině s názvem **MyToolboxControl.MyToolboxControl**. Tyto názvy můžete změnit v *souboru MyToolboxControl.xaml.cs.*

1. Otevřete *MyToolboxControl.xaml.cs* v zobrazení kódu.

2. Najděte `MyToolboxControl` třídu a přejmenujte ji na TestControl. (Nejrychlejší způsob, jak to udělat, je přejmenovat třídu, pak vyberte **přejmenovat** z kontextové nabídky a dokončit kroky. (Další informace o příkazu **Přejmenovat** najdete v tématu [Přejmenování refaktoringu (C#)](../ide/reference/rename.md).)

3. Přejděte `ProvideToolboxControl` na atribut a změňte hodnotu prvního parametru na **Test**. Toto je název skupiny, která bude obsahovat ovládací prvek v **panelu nástrojů**.

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

## <a name="build-test-and-deployment"></a>Sestavení, testování a nasazení

 Při ladění projektu, měli byste najít ovládací prvek nainstalovaný v **panelu nástrojů** experimentální instance sady Visual Studio.

### <a name="to-build-and-test-the-control"></a>Vytvoření a testování ovládacího prvku

1. Znovu sestavte projekt a začněte ladění.

2. V nové instanci sady Visual Studio vytvořte projekt aplikace WPF. Ujistěte se, že je otevřený Návrhář XAML.

3. Najděte svůj ovládací prvek v **panelu nástrojů** a přetáhněte ho na návrhovou plochu.

4. Spusťte ladění aplikace WPF.

5. Ověřte, zda se ovládací prvek zobrazuje.

### <a name="to-deploy-the-control"></a>Nasazení ovládacího prvku

1. Po sestavení testovaného projektu najdete soubor *.vsix* ve složce\* *\bin\debug projektu.

2. Můžete jej nainstalovat do místního počítače poklepáním na soubor *.vsix* a podle postupu instalace. Chcete-li ovládací prvek odinstalovat, přejděte na**položku Rozšíření a aktualizace** **nástrojů** > a vyhledejte rozšíření ovládacího prvku a klepněte na tlačítko **Odinstalovat**.

3. Nahrajte soubor *.vsix* do sítě nebo na web.

    Pokud soubor nahrajete na web [Webu Visual Studio Marketplace,](https://marketplace.visualstudio.com/) ostatní uživatelé mohou pomocí rozšíření **nástrojů** > **a aktualizací** v sadě Visual Studio najít ovládací prvek online a nainstalovat jej.

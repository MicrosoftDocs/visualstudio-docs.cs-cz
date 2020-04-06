---
title: Vytvoření ovládacího prvku panelu nástrojů formulářů systému Windows | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739583"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů formulářů systému Windows

Šablona položky Ovládací prvek panelu nástrojů systému Windows Forms, která je součástí nástroje pro rozšiřitelnost aplikace Visual Studio (VS SDK), umožňuje vytvořit ovládací prvek **panelu nástrojů,** který je automaticky přidán při instalaci rozšíření. Tento návod ukazuje, jak pomocí šablony vytvořit jednoduchý ovládací prvek čítače, který můžete distribuovat ostatním uživatelům.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Vytvoření ovládacího prvku Panelu nástrojů

Šablona Ovládací prvek panelu nástrojů windows forms vytvoří nedefinovaný uživatelský ovládací prvek a poskytuje všechny funkce, které jsou nutné k přidání ovládacího prvku do **panelu nástrojů**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Vytvoření rozšíření pomocí ovládacího prvku panelu nástrojů windows forms

1. Vytvořte projekt VSIX s názvem `MyWinFormsControl`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Po otevření projektu přidejte šablonu položky `Counter` **ovládacího prvku panelu nástrojů systému Windows Forms** s názvem . V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na možnost**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **Ovládací prvek panelu nástrojů formulářů systému Windows.**

3. Tím přidáte uživatelský ovládací `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> prvek, a umístit ovládací prvek do **panelu nástrojů**a **položku Microsoft.VisualStudio.ToolboxControl** Asset v manifestu VSIX pro nasazení.

### <a name="build-a-user-interface-for-the-control"></a>Vytvoření uživatelského rozhraní pro ovládací prvek

Ovládací `Counter` prvek vyžaduje dva <xref:System.Windows.Forms.Label> podřízené ovládací prvky: <xref:System.Windows.Forms.Button> a pro zobrazení aktuálního počtu a pro obnovení počtu na 0. Žádné další podřízené ovládací prvky jsou vyžadovány, protože volající zvýší čítač programově.

#### <a name="to-build-the-user-interface"></a>Vytvoření uživatelského rozhraní

1. V **Průzkumníku řešení**poklepejte na *Counter.cs* a otevřete jej v návrháři.

2. Odstraňte **klikněte zde!** tlačítko, které je zahrnuto ve výchozím nastavení při přidání šablony položky Ovládací prvek panelu nástrojů systému Windows Forms.

3. Z **panelu nástrojů** `Label` přetáhněte ovládací `Button` prvek a potom ovládací prvek pod ním na návrhovou plochu.

4. Změňte velikost celkového uživatelského ovládacího prvku na 150, 50 pixelů a změňte velikost ovládacího prvku tlačítka na 50, 20 pixelů.

5. V okně **Vlastnosti** nastavte následující hodnoty pro ovládací prvky na návrhové ploše.

    |Řízení|Vlastnost|Hodnota|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Název**|btnReset|
    |`Button1`|**Text**|Resetovat|

### <a name="code-the-user-control"></a>Kód uživatelského ovládacího prvku

Ovládací `Counter` prvek vystaví metodu k zvýšení čítače, událost, která má být vyvolána při každém zvýšení čítače, tlačítko **Reset** a tři vlastnosti pro uložení aktuálního počtu, zobrazovaného textu a zda se má zobrazit nebo skrýt tlačítko **Reset.** Atribut `ProvideToolboxControl` určuje, kde se v `Counter` **panelu nástrojů** zobrazí ovládací prvek.

#### <a name="to-code-the-user-control"></a>Kód uživatelského ovládacího prvku

1. Poklepáním na formulář otevřete obslužnou rutinu události zatížení v okně kódu.

2. Nad metodou obslužné rutiny události ve třídě ovládacího prvku vytvořte celé číslo pro uložení hodnoty čítače a řetězec pro uložení zobrazeného textu, jak je znázorněno v následujícím příkladu.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Vytvořte následující deklarace veřejných vlastností.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Volající mohou získat a nastavit text zobrazení čítače a zobrazit nebo skrýt tlačítko **Reset.** Volající mohou získat aktuální hodnotu vlastnosti jen pro `Value` čtení, ale nemohou nastavit hodnotu přímo.

4. Vložte následující kód `Load` do události pro ovládací prvek.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Nastavení **textu Popisek** v <xref:System.Windows.Forms.UserControl.Load> události umožňuje načíst cílové vlastnosti před použitím jejich hodnot. Nastavení **textu Popisek** v konstruktoru by mělo za následek prázdný **popisek**.

5. Vytvořte následující veřejnou metodu pro zvýšení čítače.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Přidejte deklaraci `Incremented` události do třídy ovládacího prvku.

    ```csharp
    public event EventHandler Incremented;
    ```

    Volající mohou přidat obslužné rutiny k této události reagovat na změny v hodnotě čítače.

7. Vraťte se do návrhového zobrazení a `btnReset_Click` poklepejte na tlačítko **Obnovit,** chcete-li vygenerovat obslužnou rutinu události, a vyplňte ji, jak je znázorněno v následujícím příkladu.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Bezprostředně nad definicí třídy v deklaraci atributu `ProvideToolboxControl` změňte hodnotu prvního parametru z `"MyWinFormsControl.Counter"` na `"General"`. Tím nastavíte název skupiny položek, která bude hostitelem ovládacího prvku v **panelu nástrojů**.

    Následující příklad ukazuje `ProvideToolboxControl` atribut a upravenou definici třídy.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Otestujte ovládací prvek

 Chcete-li otestovat ovládací **prvek panelu nástrojů,** nejprve jej otestujte ve vývojovém prostředí a pak jej otestujte v kompilované aplikaci.

#### <a name="to-test-the-control"></a>Chcete-li otestovat ovládací prvek

1. Stisknutím **klávesy F5** **spusťte ladění**.

    Tento příkaz vytvoří projekt a otevře druhou experimentální instanci sady Visual Studio, která má nainstalovaný ovládací prvek.

2. V experimentální instanci sady Visual Studio vytvořte projekt **aplikace Windows Forms.**

3. V **Průzkumníku řešení**poklepejte na *Form1.cs* a otevřete jej v návrháři, pokud ještě není otevřený.

4. V **panelu**nástrojů `Counter` by měl být ovládací prvek zobrazen v části **Obecné.**

5. Přetáhněte `Counter` ovládací prvek do formuláře a vyberte ho. `Value`Vlastnosti `Message`, `ShowReset` a budou zobrazeny v okně **Vlastnosti** spolu s <xref:System.Windows.Forms.UserControl>vlastnostmi, které jsou zděděny z .

6. Nastavte `Message` vlastnost `Count:`na .

7. Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek do formuláře a nastavte vlastnosti názvu `Test`a textu tlačítka na .

8. Poklepáním na tlačítko *otevřete Form1.cs* v zobrazení kódu a vytvořte obslužnou rutinu kliknutí.

9. V obslužné rutině click volejte `counter1.Increment()`.

10. Ve funkci konstruktoru zadejte `InitializeComponent`po `counter1``.``Incremented +=` volání na , zadejte a stiskněte **klávesu Tab** dvakrát.

    Visual Studio generuje obslužnou `counter1.Incremented` rutinu na úrovni formuláře pro událost.

11. Zvýrazněte `Throw` příkaz v obslužné rutině události, zadejte `mbox`a dvakrát stiskněte **klávesu Tab,** abyste vygenerovali okno se zprávou z fragmentu kódu mbox.

12. Na dalším řádku přidejte `if` / `else` následující blok a nastavte viditelnost tlačítka **Reset.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Stiskněte **klávesu F5**.

    Formulář se otevře. Ovládací `Counter` prvek zobrazí následující text.

    **Počet: 0**

14. Klepněte na tlačítko **Testovat**.

    Čítač přírůstky a Visual Studio zobrazí okno se zprávou.

15. Zavřete okno se zprávou.

    Tlačítko **Obnovit** zmizí.

16. Klikněte na **Testovat,** dokud počítadlo nedosáhne **5** a pokaždé zavře okna se zprávami.

    Znovu se zobrazí tlačítko **Obnovit.**

17. Klepněte na tlačítko **Obnovit**.

    Počítadlo se resetuje na **0**.

## <a name="next-steps"></a>Další kroky

Při vytváření ovládacího prvku **Panelu nástrojů** vytvoří aplikace Visual Studio soubor s názvem *Název_všest* ve složce \bin\debug\ projektu. Ovládací prvek můžete nasadit nahráním souboru *.vsix* do sítě nebo na web. Když uživatel otevře soubor *.vsix,* ovládací prvek je nainstalován a přidán do **panelu nástrojů** sady Visual Studio v počítači uživatele. Případně můžete nahrát soubor *.vsix* na [tržiště sady Visual Studio,](https://marketplace.visualstudio.com/) aby ho uživatelé mohli najít procházením v dialogovém okně Rozšíření a aktualizace **nástrojů.** > **Extensions and Updates**

## <a name="see-also"></a>Viz také

- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Vytvoření ovládacího prvku WPF Toolbox](../extensibility/creating-a-wpf-toolbox-control.md)
- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Základy vývoje řízení systému Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)

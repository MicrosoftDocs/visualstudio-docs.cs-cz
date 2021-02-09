---
title: Vytvoření ovládacího prvku panelu nástrojů model Windows Forms | Microsoft Docs
description: Tento návod ukazuje, jak použít šablonu ovládacího prvku panelu nástrojů model Windows Forms k vytvoření jednoduchého ovládacího prvku čítače pomocí sady Visual Studio SDK.
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4bb9505ab475da7919a39eb03e7c84b92857db4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902188"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů model Windows Forms

Šablona položky ovládacího prvku sady nástrojů model Windows Forms, která je součástí Visual Studio Extensibility Tools (VS SDK), umožňuje vytvořit ovládací prvek **sady nástrojů** , který se automaticky přidá při instalaci rozšíření. Tento návod ukazuje, jak použít šablonu k vytvoření jednoduchého ovládacího prvku čítače, který můžete distribuovat dalším uživatelům.

## <a name="prerequisites"></a>Požadavky

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů

Šablona ovládacího prvku panelu nástrojů model Windows Forms vytvoří nedefinovaný uživatelský ovládací prvek a poskytne všem funkcím, které jsou požadovány pro přidání ovládacího prvku do **sady nástrojů**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Vytvoření rozšíření pomocí model Windows Forms ovládacího prvku panelu nástrojů

1. Vytvořte projekt VSIX s názvem `MyWinFormsControl` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** , a to tak, že vyhledáte "VSIX".

2. Po otevření projektu přidejte šablonu položky **ovládacího prvku panelu nástrojů model Windows Forms** s názvem `Counter` . V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** přejít na rozšiřitelnost **Visual C#**  >   a vybrat **model Windows Forms ovládací prvek panelu nástrojů**

3. Tím přidáte uživatelský ovládací prvek, který `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> umístí ovládací prvek do **panelu nástrojů**, a položku **Microsoft. VisualStudio. ToolboxControl** Asset v manifestu VSIX pro nasazení.

### <a name="build-a-user-interface-for-the-control"></a>Sestavení uživatelského rozhraní pro ovládací prvek

`Counter`Ovládací prvek vyžaduje dva podřízené ovládací prvky: a <xref:System.Windows.Forms.Label> k zobrazení aktuálního počtu a <xref:System.Windows.Forms.Button> k resetování počtu na 0. Nejsou vyžadovány žádné další podřízené ovládací prvky, protože volající zvýší čítač programově.

#### <a name="to-build-the-user-interface"></a>Sestavení uživatelského rozhraní

1. V **Průzkumník řešení** poklikejte na *Counter.cs* a otevře se v návrháři.

2. Odeberte **kliknutím sem.** tlačítko, které je součástí výchozího nastavení, když přidáte šablonu ovládacího prvku model Windows Forms panelu nástrojů.

3. Z **panelu nástrojů** přetáhněte `Label` ovládací prvek a potom `Button` pod ním ovládací prvek na návrhovou plochu.

4. Změňte velikost celkového uživatelského ovládacího prvku na 150, 50 pixelů a změňte velikost ovládacího prvku tlačítko na 50, 20 pixelů.

5. V okně **vlastnosti** nastavte následující hodnoty pro ovládací prvky na návrhové ploše.

    |Řízení|Vlastnost|Hodnota|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Název**|btnReset|
    |`Button1`|**Text**|Resetovat|

### <a name="code-the-user-control"></a>Kódování uživatelského ovládacího prvku

`Counter`Ovládací prvek vystaví metodu pro zvýšení čítače, událost, která má být vyvolána při každém zvýšení čítače, tlačítko **resetování** a tři vlastnosti pro uložení aktuálního počtu, zobrazeného textu a určuje, zda má být zobrazeno nebo skryto tlačítko pro **obnovení** . `ProvideToolboxControl`Atribut určuje, kde se ovládací prvek zobrazí v **sadě nástrojů** `Counter` .

#### <a name="to-code-the-user-control"></a>Pro kód uživatelského ovládacího prvku

1. Dvojím kliknutím na formulář otevřete jeho obslužnou rutinu události načtení v okně Code (kód).

2. Nad metodou obslužné rutiny události, ve třídě ovládacího prvku, vytvořte celé číslo pro uložení hodnoty čítače a řetězec pro uložení zobrazovaného textu, jak je znázorněno v následujícím příkladu.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Vytvořte následující deklarace veřejných vlastností.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Volající mají přístup k těmto vlastnostem k získání a nastavení zobrazovaného textu čítače a k zobrazení nebo skrytí tlačítka pro **obnovení** . Volající mohou získat aktuální hodnotu vlastnosti jen pro čtení `Value` , ale nemohou hodnotu přímo nastavit.

4. Do `Load` události pro ovládací prvek vložte následující kód.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Nastavení textu **popisku** v <xref:System.Windows.Forms.UserControl.Load> události umožní načíst cílové vlastnosti před použitím jejich hodnot. Nastavení textu **popisku** v konstruktoru má za následek prázdný **popisek**.

5. Vytvořte následující veřejnou metodu, která zvýší čítač.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Přidejte do `Incremented` třídy ovládacího prvku deklaraci události.

    ```csharp
    public event EventHandler Incremented;
    ```

    Volající mohou přidat do této události obslužné rutiny, aby reagovaly na změny v hodnotě čítače.

7. Vraťte se do návrhového zobrazení a dvakrát klikněte na tlačítko **obnovit** pro vygenerování `btnReset_Click` obslužné rutiny události. Pak ho vyplňte tak, jak je znázorněno v následujícím příkladu.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Přímo nad definicí třídy, v `ProvideToolboxControl` deklaraci atributu změňte hodnotu prvního parametru z `"MyWinFormsControl.Counter"` na `"General"` . Tím se nastaví název skupiny položek, která bude hostovat ovládací prvek v **sadě nástrojů**.

    Následující příklad ukazuje `ProvideToolboxControl` atribut a upravenou definici třídy.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testování ovládacího prvku

 Chcete-li otestovat ovládací prvek **sady nástrojů** , nejprve ho otestujte ve vývojovém prostředí a pak ho otestujte v kompilované aplikaci.

#### <a name="to-test-the-control"></a>Testování ovládacího prvku

1. Stisknutím  klávesy F5 **Spusťte ladění**.

    Tento příkaz sestaví projekt a otevře druhou experimentální instanci sady Visual Studio s nainstalovaným ovládacím prvkem.

2. V experimentální instanci aplikace Visual Studio vytvořte projekt **aplikace model Windows Forms** .

3. V **Průzkumník řešení** dvakrát klikněte na *Form1.cs* a otevřete ho v návrháři, pokud ještě není otevřený.

4. V sadě **nástrojů** `Counter` by měl být ovládací prvek zobrazen v části **Obecné** .

5. Přetáhněte `Counter` ovládací prvek do formuláře a vyberte jej. `Value`Vlastnosti, `Message` a `ShowReset` se zobrazí v okně **vlastnosti** spolu s vlastnostmi děděnými z <xref:System.Windows.Forms.UserControl> .

6. Nastavte `Message` vlastnost na hodnotu `Count:` .

7. Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek do formuláře a potom nastavte vlastnosti název a text tlačítka na `Test` .

8. Dvojím kliknutím na tlačítko otevřete *Form1.cs* v zobrazení kódu a vytvořte obslužnou rutinu Click.

9. V obslužné rutině Click volejte `counter1.Increment()` .

10. Ve funkci konstruktoru po volání do `InitializeComponent` Zadejte `counter1``.``Incremented +=` a potom stiskněte klávesu **TAB** dvakrát.

    Visual Studio vygeneruje obslužnou rutinu na úrovni formuláře pro `counter1.Incremented` událost.

11. Zvýrazněte `Throw` příkaz v obslužné rutině události, zadejte `mbox` a potom stiskněte klávesu **TAB** dvakrát pro vygenerování zprávy z fragmentu kódu mbox.

12. Na dalším řádku přidejte následující `if` / `else` blok pro nastavení viditelnosti tlačítka **obnovit** .

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Stiskněte klávesu **F5**.

    Otevře se formulář. `Counter`Ovládací prvek zobrazí následující text.

    **Počet: 0**

14. Vyberte **Test**.

    Čítač zvýší a aplikace Visual Studio zobrazí okno se zprávou.

15. Zavřete okno se zprávou.

    Tlačítko **resetování** zmizí.

16. Vyberte **test** , dokud počítadlo nedosáhne **5** zavření oken zpráv.

    Znovu se zobrazí tlačítko **resetovat** .

17. Vyberte **Resetovat**.

    Čítač obnoví **hodnotu na 0**.

## <a name="next-steps"></a>Další kroky

Když sestavíte ovládací prvek **sady nástrojů** , sada Visual Studio vytvoří soubor s názvem *ProjectName. vsix* ve složce \bin\debug\ projektu. Ovládací prvek lze nasadit nahrajte tak, že nahrajete soubor *. vsix* do sítě nebo na web. Když uživatel otevře soubor *. vsix* , ovládací prvek se nainstaluje a přidá do **sady nástrojů** Visual Studio v počítači uživatele. Případně můžete odeslat soubor *. vsix* do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , aby ho uživatelé mohli najít v   >  dialogovém okně **rozšíření a aktualizace** nástrojů.

## <a name="see-also"></a>Viz také

- [Rozšiřování dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Vytvoření ovládacího prvku sady nástrojů WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Rozšiřování dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Základy vývoje model Windows Forms ovládacích prvků](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)

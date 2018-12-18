---
title: Vytváření Windows Forms ovládacího prvku panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a44dfd224324ba641e70e0cfe6ded87f88fe6765
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307701"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Vytvoření ovládacího prvku Windows Forms panel nástrojů
Šablona položky ovládacího prvku Windows Forms panel nástrojů, který je součástí aplikace Visual Studio Extensibility Tools (VS SDK) umožňuje vytvořit ovládací prvek, který je automaticky přidán do **nástrojů** při instalaci rozšíření. Toto téma ukazuje, jak použít šablonu k vytvoření ovládacího prvku jednoduchého čítače, které můžete distribuovat ostatním uživatelům.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-windows-forms-toolbox-control"></a>Vytvoření ovládacího prvku Windows Forms panel nástrojů  
 Šablony ovládacího prvku Windows Forms panel nástrojů vytvoří nedefinované uživatelský ovládací prvek a poskytuje všechny funkce, které je povinné pro přidání ovládacího prvku, aby **nástrojů**.  
  
### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Vytvoření rozšíření pomocí ovládacího prvku Windows Forms panel nástrojů  
  
1.  Vytvořte projekt VSIX s názvem `MyWinFormsControl`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C#** > **rozšiřitelnost**.  
  
2.  Po otevření projektu, přidejte **ovládacího prvku Windows Forms panel nástrojů** šablony položky s názvem `Counter`. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C#** > **rozšiřitelnost** a vyberte **ovládacího prvku Windows Forms panelu nástrojů**  
  
3.  Tento postup přidá uživatelský ovládací prvek, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> umístit ovládacího prvku **nástrojů**a **Microsoft.VisualStudio.ToolboxControl** položku prostředku v manifestu VSIX pro nasazení.  
  
### <a name="build-a-user-interface-for-the-control"></a>Vytvoření uživatelského rozhraní pro ovládací prvek  
 `Counter` Ovládací prvek požaduje dva podřízené ovládací prvky: <xref:System.Windows.Forms.Label> zobrazíte aktuální počet a <xref:System.Windows.Forms.Button> obnovit počet na hodnotu 0. Žádné další podřízené ovládací prvky jsou povinné, protože volající, zvýší čítač prostřednictvím kódu programu.  
  
#### <a name="to-build-the-user-interface"></a>K vytvoření uživatelského rozhraní  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel *Counter.cs* ho otevřete v návrháři.  
  
2.  Odeberte **klikněte sem!** tlačítko, které je zahrnuté ve výchozím nastavení při přidání šablony položky ovládacího prvku Windows Forms panelu nástrojů.  
  
3.  Z **nástrojů**, přetáhněte `Label` ovládací prvek a potom `Button` ovládacího prvku pod ním na návrhové ploše.  
  
4.  Změnit velikost celkového uživatelského ovládacího prvku na 150, 50 pixelů a změnu velikosti panelu ovládacího prvku na 50, 20 pixelů.  
  
5.  V **vlastnosti** okno, nastavte následující hodnoty pro ovládací prvky na návrhové ploše.  
  
    |Ovládací prvek|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |`Label1`|**Text**|""|  
    |`Button1`|**Název**|btnReset|  
    |`Button1`|**Text**|Resetovat|  
  
### <a name="code-the-user-control"></a>Kód uživatelského ovládacího prvku  
 `Counter` Ovládací prvek bude vystavovat metodu se zvýší čítač událost vyvolána pokaždé, když hodnota čítače se zvýší, **resetování** tlačítko a tři vlastnosti pro ukládání aktuální počet zobrazení textu a, jestli se má zobrazit nebo skrýt **resetování** tlačítko. `ProvideToolboxControl` Atribut určí, kde v **nástrojů** `Counter` ovládací prvek zobrazí.  
  
#### <a name="to-code-the-user-control"></a>Do kódu uživatelského ovládacího prvku  
  
1.  Poklepejte na formulář v okně kódu otevřete své obslužné rutině události load.  
  
2.  Nad metodu obslužné rutiny události vytvoření ve třídě ovládacího prvku celé číslo k uložení hodnota čítače a řetězec pro uložení zobrazení textu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Vytvořte následující veřejnou vlastnost deklarace.  
  
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
  
     Volající může zobrazit tyto vlastnosti k získání a nastavení zobrazení textu čítače a chcete zobrazit nebo skrýt **resetování** tlačítko. Volající může získat aktuální hodnotu jen pro čtení `Value` vlastností, ale nelze nastavit hodnotu přímo.  
  
4.  Vložte následující kód `Load` události pro ovládací prvek.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Nastavení **popisek** text <xref:System.Windows.Forms.UserControl.Load> událostí umožňuje vlastnosti cíle pro načtení před jejich hodnoty se použijí. Nastavení **popisek** text v konstruktoru by mělo za následek prázdnou **popisek**.  
  
5.  Vytvořte následující veřejnou metodu pro zvýšení čítače.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Přidat deklaraci `Incremented` událostí na třídě ovládacího prvku.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Volající může přidat obslužné rutiny na tuto událost reakce na změny v hodnotě čítače.  
  
7.  Vraťte se do návrhového zobrazení a dvakrát klikněte **resetování** pro vygenerování `btnReset_Click` obslužná rutina události a vyplňte v, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Přímo nad definici třídy v `ProvideToolboxControl` atribut deklarace, změňte hodnotu z prvního parametru `"MyWinFormsControl.Counter"` k `"General"`. Tím se nastaví na název skupiny položky, který bude hostitelem ovládacího prvku **nástrojů**.  
  
     Následující příklad ukazuje `ProvideToolboxControl` atribut a definice upravené třídy.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="test-the-control"></a>Testování ovládacího prvku  
 K testování **nástrojů** řídit, nejprve ji otestovat ve vývojovém prostředí a pak ho otestujte v kompilované aplikace.  
  
#### <a name="to-test-the-control"></a>Testování ovládacího prvku  
  
1.  Stisknutím klávesy **F5**.  
  
     To vytvoří projekt a otevře se druhá experimentální instanci sady Visual Studio, který má ovládací prvek nainstalovaný.  
  
2.  V experimentální instanci sady Visual Studio, vytvořit **formulářová aplikace Windows** projektu.  
  
3.  V **Průzkumníka řešení**, dvakrát klikněte na panel *Form1.cs* otevřete v návrháři, pokud ještě není otevřený.  
  
4.  V **nástrojů**, `Counter` ovládací prvek má být zobrazen v **Obecné** oddílu.  
  
5.  Přetáhněte `Counter` do svého formuláře ovládací prvek a vyberte ji. `Value`, `Message`, A `ShowReset` vlastnosti se zobrazí v **vlastnosti** okno spolu s vlastnostmi, která jsou zděděna z <xref:System.Windows.Forms.UserControl>.  
  
6.  Nastavte `Message` vlastnost `Count:`.  
  
7.  Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek na formuláři a potom nastavte vlastnosti name a text tlačítka `Test`.  
  
8.  Dvakrát klikněte na tlačítko Otevřít *Form1.cs* v zobrazení kódu a vytvořte obslužnou rutinu kliknutí.  
  
9. Obslužné rutiny kliknutí, volejte `counter1.Increment()`.  
  
10. Ve funkci konstruktoru po volání `InitializeComponent`, typ `counter1``.``Incremented +=` a potom stiskněte klávesu **kartu** dvakrát.  
  
     Visual Studio vygeneruje obslužnou rutinu úrovni formuláře `counter1.Incremented` událostí.  
  
11. Zvýrazněte `Throw` příkaz v obslužné rutině události, typ `mbox`a potom stiskněte klávesu **kartu** dvakrát ke generování okno se zprávou z mbox fragmentu kódu.  
  
12. Na dalším řádku, přidejte následující `if` / `else` bloku nastavit, zda **resetování** tlačítko.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Stisknutím klávesy **F5**.  
  
     Otevře se formulář. `Counter` Ovládací prvek zobrazuje následující text.  
  
     **Počet: 0**  
  
14. Klikněte na tlačítko **Test**.  
  
     Zvýší čítače a sady Visual Studio zobrazí okno se zprávou.  
  
15. Zavřete okno se zprávou.  
  
     **Resetování** tlačítko zmizí.  
  
16. Klikněte na tlačítko **testovací** dokud nedosáhne čítač **5** zavření zprávy pole pokaždé, když.  
  
     **Resetování** tlačítko se znovu zobrazí.  
  
17. Klikněte na tlačítko **resetování**.  
  
     Čítač obnoví **0**.  
  
## <a name="next-steps"></a>Další kroky  
 Při sestavení **nástrojů** ovládací prvek, Visual Studio vytvoří soubor s názvem *ProjectName.vsix* \bin\debug\ složky vašeho projektu. Ovládací prvek můžete nasadit tak, že nahrajete *VSIX* soubor k síti nebo na web. Když uživatel otevře *VSIX* soubor, ovládací prvek je nainstalován a přidali do sady Visual Studio **nástrojů** na počítači uživatele. Alternativně můžete nahrát *VSIX* do souboru [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkID=123847) tak, aby uživatelé můžete najít tak, že přejdete v **nástroje**  >   **Rozšíření a aktualizace** dialogového okna.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Vytvoření ovládacího prvku panel nástrojů WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Základní informace o vývoji pro ovládací prvek Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)

---
title: Testování aplikací pro UWP pomocí programových testů uživatelského rozhraní
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 3dcbd6065d45bf5350b80d555f335d3b8ec1cec7
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895961"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Vytvoření programového uživatelského rozhraní testu aplikace pro UPW

Tento článek vysvětluje, jak vytvořit programový test uživatelského rozhraní pro aplikace univerzální platformy Windows (UPW).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Vytvoření aplikace pro UPW pro testování

Prvním krokem je vytvoření jednoduché aplikace pro UPW pro spuštění testu oproti.

1. V sadě Visual Studio vytvořte nový projekt pomocí **prázdná aplikace (Universal Windows)** šablony Visual C# nebo Visual Basic.

     ![Šablona prázdná aplikace Universal Windows](../test/media/blank-uwp-app-template.png)

1. V **nový projekt univerzální platformy Windows** dialogového okna, vyberte **OK** přijměte výchozí verze platformy.

1. Z **Průzkumníka řešení**, otevřete *MainPage.xaml*.

   Soubor se otevře v **návrháře XAML**.

1. Přetáhněte ovládací prvek button a ovládací prvek textového pole z **nástrojů** na návrhovou plochu.

     ![Návrh aplikace pro UPW](../test/media/toolbox-controls.png)

1. Zadejte názvy ovládacích prvků. Vyberte ovládací prvek textového pole a pak v **vlastnosti** okno, zadejte **textového pole** v **název** pole. Vyberte ovládací prvek tlačítko a pak v **vlastnosti** okno, zadejte **tlačítko** v **název** pole.

1. Poklepejte na ovládací prvek tlačítko a přidejte následující kód do těla `Button_Click` metody. Tento kód jednoduše nastaví text do textového pole název ovládacího prvku tlačítko, stačí, abyste nám řekli něco, co můžete ověřit pomocí programového testu uživatelského rozhraní, který vytvoříme později.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Stisknutím klávesy **Ctrl**+**F5** ke spuštění aplikace. By měl vypadat přibližně takto:

   ![Aplikace pro UPW s tlačítko a textové pole](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Vytvořit programový test uživatelského rozhraní

1. Přidat projekt testu k řešení, klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **přidat** > **nový projekt**.

1. V **nový projekt** dialogového okna, vyberte **projekt programového testu UI (Universal Windows)** šablony. Můžete najít v šabloně **Windows Universal** kategorie v části **Visual C#** nebo **jazyka Visual Basic**.

     ![Nový projekt programového testu UI](../test/media/coded-ui-test-project-uwp-template.png)

   > [!NOTE]
   > Pokud se nezobrazí **projekt programového uživatelského rozhraní testu (Universal Windows)** šablony, budete muset [nainstalovat komponentu programového testu uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. V **generovat kód pro programový Test uživatelského rozhraní** dialogového okna, vyberte **upravit test ručně**.

     ![Generovat kód pro programový test dialogové okno uživatelského rozhraní](../test/media/manually-edit-the-test.png)

1. Pokud vaše aplikace pro UPW není spuštěná, spusťte ji stisknutím klávesy **Ctrl**+**F5**.

1. Otevřít **Tvůrce programového testu UI** dialogové okno tak, že kurzor umístíte `CodedUITestMethod1` metodu a poté volbou **testovací** > **generovat kód pro programový Test uživatelského rozhraní**  >  **Použití Tvůrce programového testu UI**.

1. Přidáte ovládací prvky v mapování ovládacího prvku uživatelského rozhraní. Použití **Tvůrce programového testu UI** nástroj nitkového kříže vyberte ovládací prvek tlačítko v aplikaci pro UPW. V **přidat kontrolní výrazy** dialogového okna, rozbalte **mapování ovládacího prvku UI** podokně Pokud nezbytné a pak vyberte **přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.

     ![Přidat ovládací prvek do mapy uživatelského rozhraní](../test/media/add-control-to-ui-control-map.png)

1. Opakujte předchozí krok a přidejte ovládací prvek textbox do mapování ovládacích prvků uživatelského rozhraní.

1. V **Tvůrce programového testu UI** dialogového okna, vyberte **generovat kód** nebo stiskněte klávesu **Ctrl**+**G**. Potom vyberte **generovat** vytvořit kód pro změny mapování ovládacího prvku uživatelského rozhraní.

     ![Generování kódu pro mapování uživatelského rozhraní](../test/media/generate-code-dialog.png)

1. Chcete-li ověřit, že se text v textovém poli změní na **tlačítko** při kliknutí na tlačítko, klikněte na tlačítko.

     ![Klikněte na tlačítko Nastavit hodnotu pole textbox](../test/media/uwp-app-button-textbox.png)

1. Přidáte kontrolní výraz k ověření textu v ovládacím prvku textbox. Pomocí nástroje nitkového kříže vyberte ovládací prvek textového pole a pak vyberte **Text** vlastnost **přidat kontrolní výrazy** dialogového okna. Vyberte **přidat kontrolní výraz** nebo stiskněte klávesu **Alt**+**A**. V **zpráva o selhání kontrolního výrazu** zadejte **hodnotu pole Textbox neočekávaný.** a pak vyberte **OK**.

     ![Zvolte textové pole s nitkového kříže a přidat kontrolní výraz](../test/media/add-assertion-for-text.png)

1. Generuje kód testu kontrolního výrazu. V **Tvůrce programového testu UI** dialogového okna, vyberte **generovat kód**. V **generovat kód** dialogového okna, vyberte **přidat a vytvořit**.

     ![Generovat kód pro textové pole kontrolního výrazu](../test/media/add-and-generate-assert-method.png)

   V **Průzkumníka řešení**, otevřete *UIMap.Designer.cs* zobrazení přidaného kódu pro metodu assert a ovládací prvky.

   > [!TIP]
   > Pokud používáte jazyk Visual Basic, otevřete *CodedUITest1.vb*. Potom v `CodedUITestMethod1()` kódu metody testování, klikněte pravým tlačítkem na volání metody assert `Me.UIMap.AssertMethod1()` a zvolte **přejít k definici**. *UIMap.Designer.vb* otevře v editoru kódu a můžete zobrazení přidaného kódu pro metodu assert a ovládací prvky.

    > [!WARNING]
    > Neprovádějte žádné změny *UIMap.designer.cs* nebo *UIMap.Designer.vb* soubory přímo. Pokud tak učiníte, vaše změny budou přepsány, když je generován test.

    Metoda assert vypadá takto:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```
1. Dále musíme získat **AutomationId** aplikace UPW [aplikace](#create-a-uwp-app-to-test) , které chceme otestovat. Otevřete Windows **Start** nabídku zobrazte dlaždici aplikace. Tažením nástroje vlasového kříže ![cílovou ikonu](media/target-icon.png) z **Tvůrce programového testu UI** dialogového okna na dlaždici pro vaši aplikaci. Když modrá úchyty na dlaždici, uvolněte myší.

   ![Nástroj nitkového kříže](media/cross-hair-tool.png)

   **Přidat kontrolní výrazy** dialogové okno se otevře a zobrazí **AutomationId** pro vaši aplikaci. Klikněte pravým tlačítkem na **AutomationId** a zvolte **Kopírovat hodnotu do schránky**.

   ![AutomationID v dialogovém okně Přidat kontrolní výraz](../test/media/automation-id.png)

1. Přidejte kód do metody testu pro spuštění aplikace UPW. V **Průzkumníka řešení**, otevřete *CodedUITest1.cs* nebo *CodedUITest1.vb*. Nad volání `AssertMethod1`, přidejte kód pro spuštění aplikace pro UPW:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   ID služby automation v příkladu kódu nahraďte hodnotou, kterou jste zkopírovali do schránky. v předchozím kroku.

   > [!IMPORTANT]
   > Zkrátit začátek ID automatizace odebrání znaky, jako **P ~**. Pokud není trim tyto znaky, vyvolá testu `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` při pokusu o spuštění aplikace.

1. V dalším kroku přidejte kód do metody testu na tlačítko. Na řádku po `XamlWindow.Launch`, přidejte gesto pro klepnutí na ovládací prvek tlačítka:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po přidání kódu, kompletní `CodedUITestMethod1` testovací metoda by měla vypadat následovně:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Vytvoření testovacího projektu a pak otevřete **Průzkumníka testů** tak, že vyberete **testování** > **Windows** > **Průzkumníka testů**.

1. Vyberte **spustit všechny** pro spuštění testu.

   Aplikace otevře na tlačítko klepnutí a textového pole **Text** vyplní vlastnost. Metoda assert ověří textovém poli **Text** vlastnost.

   Po dokončení testu **Průzkumníka testů** zobrazí, že test proběhl úspěšně.

   ![Úspěšných testů se zobrazí v Průzkumníku testů](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Dotazy a odpovědi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Otázka: Proč nevidím možnost zaznamenat Moje programový test uživatelského rozhraní v generování kódu pro dialogové okno programový Test uživatelského rozhraní?

**A**: pro aplikace pro UPW není podporována možnost záznamu.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Dotaz: lze vytvořit programový test uživatelského rozhraní pro mé aplikace UWP založené na WinJS?

**A**: Ne, jsou podporovány pouze aplikací založených na XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nelze upravit kód v souboru UIMap.Designer?

**A**: všechny změny provedené v kódu *UIMapDesigner.cs* souboru budou přepsány pokaždé, když vygenerujete pomocí kódu **Tvůrce programového testu UI**. Pokud je třeba změnit zaznamenanou metodu, zkopírujte ho do *UIMap.cs* souboru a přejmenujte jej. *UIMap.cs* soubor lze použít k přepsání metod a vlastností v *UIMapDesigner.cs* souboru. Odebrat odkaz na původní metodu v *CodedUITest.cs* soubor a nahradit ji názvem přejmenované metody.

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Nastavit vlastnosti jedinečné automatizace pro ovládacích prvků UPW](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
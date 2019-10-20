---
title: Testování aplikací pro Windows UWP a 8,1 Store pomocí programových testů uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce4c6ceec9489abcd3573c126aefe98a268187c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660432"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Testování aplikací pro UPW a Windows 8.1 pro Store pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod použijte pro vytváření testů uživatelského rozhraní pro aplikace pro UWP a aplikace pro Store 8,1 založené na XAML.

## <a name="create-a-simple-windows-store-app"></a>Vytvoření jednoduché aplikace pro Windows Store

1. Chcete-li spustit programové testy uživatelského rozhraní pro aplikaci Windows Store založené na jazyce XAML, je nutné [nastavit jedinečnou vlastnost automatizace, která identifikuje každý ovládací prvek](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).

     V nabídce **nástroje** přejděte na **Možnosti** a pak zvolte **textový editor**, potom **XAML**a nakonec **jiné**.

     Zaškrtněte políčko pro automatické pojmenování interaktivních prvků při vytváření.

     ![Různé možnosti XAML](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

2. Vytvořte nový projekt pro prázdnou aplikaci Windows Store založenou na XAML pomocí šablony vizuálu C# nebo Visual Basic.

     ![Vytvoření formátu XAML prázdné aplikace &#40;pro Windows Store&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")

3. V Průzkumník řešení otevřete MainPage. XAML. Z panelu nástrojů přetáhněte ovládací prvek tlačítko a ovládací prvek TextBox na návrhovou plochu.

     ![Návrh aplikace pro Windows Store](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")

4. Dvakrát klikněte na ovládací prvek tlačítko a přidejte následující kód:

    ```csharp
    private void button_Click_1(object sender, RoutedEventArgs e)
    {
        this.textBox.Text = this.button.Name;
    }

    ```

    ```vb
    Public NotInheritable Class MainPage
        Inherits Page

        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click
            Me.textBox.Text = Me.button.Name
        End Sub
    End Class
    ```

5. Stisknutím klávesy F5 spusťte aplikaci pro Windows Store.

## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Vytvoření a spuštění kódovaného testu uživatelského rozhraní pro aplikaci pro Windows Store

[Návody vytvořit programové testy uživatelského rozhraní pro aplikace Univerzální platforma Windows (UWP)?](#uwpapps)

1. Vytvořte nový projekt programového testu uživatelského rozhraní pro aplikaci pro Windows Store.

    ![Nové programové uživatelské rozhraní TET &#40;projektu Windows Store&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")

2. Vyberte, chcete-li upravit mapu uživatelského rozhraní pomocí nástroje křížového vlasování.

    ![Výběr možnosti Upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")

3. Pomocí nástroje křížového navýšení v Tvůrci programového testu UI vyberte dlaždici aplikace, klikněte pravým tlačítkem na **AutomationId** a zvolte **Kopírovat hodnotu do schránky**. Hodnota ve schránce bude použita později pro zápis akce pro spuštění aplikace pro testování.

    ![Kopírovat AutomationId do schránky](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")

4. Ve spuštěné aplikaci pro Windows Store použijte k výběru ovládacího prvku tlačítko a ovládacího prvku TextBox Nástroj pro křížové vlasy. Po přidání každého ovládacího prvku vyberte tlačítko **Přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní** na panelu nástrojů Tvůrce programového testu UI.

    ![Přidat ovládací prvek do mapy uživatelského rozhraní](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")

5. Zvolte tlačítko **generovat kód** na panelu nástrojů Tvůrce programového testu UI a pak zvolte možnost vytvořit, **Chcete-li** vytvořit kód pro změny mapování ovládacího prvku uživatelského rozhraní.

    ![Vygenerovat kód pro mapu uživatelského rozhraní](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")

6. Klikněte na tlačítko a nastavte hodnotu v textovém poli.

    ![Pro nastavení hodnoty TextBox klikněte na tlačítko ovládací prvek tlačítko](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")

7. Pomocí nástroje pro křížové vlasy vyberte ovládací prvek TextBox a potom vyberte vlastnost **text** .

    ![Vyberte vlastnost text](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")

8. Přidat kontrolní výraz. V testu bude použit k ověření, zda je hodnota správná.

    ![Výběr testbox pomocí křížového&#45;vlasů a přidání kontrolního výrazu](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")

9. Přidejte a vygenerujte kód pro kontrolní výraz.

     ![Vygenerovat kód pro kontrolní výraz TextBox](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")

10. **Visual C#**

     V Průzkumník řešení otevřete soubor UIMap.Designer.cs, abyste zobrazili přidaný kód pro metodu Assert a ovládací prvky.

     **Visual Basic**

     V Průzkumník řešení otevřete soubor CodedUITest1. vb a potom v kódu metody CodedUITestMethod1 (), klikněte pravým tlačítkem myši na volání metody assertion, které bylo automaticky přidáno `Me.UIMap.AssertMethod1()` a zvolte možnost **Přejít k definici**. Tím se otevře soubor UIMap. Designer. vb v editoru kódu, abyste si mohli zobrazit přidaný kód pro metodu Assert a ovládací prvky.

    > [!WARNING]
    > Neupravujte soubor UIMap.designer.cs nebo UIMap. Designer. vb přímo. Pokud to uděláte, změny v souboru budou přepsány pokaždé, když je test vygenerován.

     **Assert – metoda**

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Ovládací prvky**

    ```csharp
    #region Properties
    public XamlButton UIButtonButton
    {
        get
        {
            if ((this.mUIButtonButton == null))
            {
                this.mUIButtonButton = new XamlButton(this);
                #region Search Criteria
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";
                this.mUIButtonButton.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUIButtonButton;
        }
    }

    public XamlEdit UITextBoxEdit
    {
        get
        {
            if ((this.mUITextBoxEdit == null))
            {
                this.mUITextBoxEdit = new XamlEdit(this);
                #region Search Criteria
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";
                this.mUITextBoxEdit.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUITextBoxEdit;
        }
    }
    #endregion

    #region Fields
    private XamlButton mUIButtonButton;

    private XamlEdit mUITextBoxEdit;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
                Me.mUIButtonButton.WindowTitles.Add("App2")
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
                Me.mUITextBoxEdit.WindowTitles.Add("App2")
            End If
            Return Me.mUITextBoxEdit
        End Get
    End Property
    #End Region

    #Region "Fields"
    Private mUIButtonButton As XamlButton

    Private mUITextBoxEdit As XamlEdit
    #End Region
    ```

11. V Průzkumník řešení otevřete soubor CodedUITest1.cs nebo CodedUITest1. vb. Nyní můžete přidat kód do metody CodedUTTestMethod1 pro akce potřebné ke spuštění testu pomocí ovládacích prvků přidaných do UIMap:

    1. Spusťte aplikaci pro Windows Store pomocí vlastnosti Automation ID, kterou jste zkopírovali do schránky dříve:

       ```csharp
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")
       ```

       ```vb
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");
       ```

    2. Přidejte gesto klepnutím na ovládací prvek tlačítko:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)
       ```

    3. Ověřte, že volání metody Assert, která byla automaticky vygenerována, přichází po spuštění aplikace a klepnutí na gesto na tlačítku:

       ```csharp
       this.UIMap.AssertMethod1();
       ```

       ```vb
       Me.UIMap.AssertMethod1()
       ```

       Po přidání kódu by se měla metoda CodedUITestMethod1 test zobrazit takto:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.

        // Launch the app.
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest(CodedUITestType.WindowsStore)>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '

            ' Launch the app.
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

12. Sestavte test a potom spusťte test pomocí Průzkumníka testů.

     ![Spuštění kódovaného testu uživatelského rozhraní z Průzkumníka testů](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")

     Spustí se aplikace pro Windows Store, akce klepnutí na tlačítko je dokončená a vlastnost text textového pole se vyplní a ověří pomocí metody Assert.

     ![Spuštění programového testu uživatelského rozhraní](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")

     Po dokončení testu zobrazí Průzkumník testů, že test proběhl úspěšně.

     ![Úspěšná zobrazení testů v Průzkumníku testů](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")

## <a name="q--a"></a>Otázka & A

- **Otázka: Proč se mi nezobrazuje možnost zaznamenat programový test uživatelského rozhraní v dialogovém okně generovat kód pro programový test UI?**

     Odpověď **: možnost**záznamu není podporována pro aplikace pro Windows Store.

- **Otázka: mohu vytvořit programový test uživatelského rozhraní pro moje aplikace pro Windows Store založené na WinJS?**

     Odpověď: Ne, podporují se jenom aplikace **založené na XAML**.

- **Otázka: mohu vytvořit programové testy uživatelského rozhraní pro aplikace pro Windows Store v systému, na kterém není spuštěný Windows 8.1 nebo Windows 10?**

     Odpověď **: ne**, šablony projektu programového testu uživatelského rozhraní jsou k dispozici pouze na Windows 8.1 a Windows 10. Abyste mohli vytvářet aplikace automatizace pro Univerzální platforma Windows (UWP), budete potřebovat Windows 10.

<a name="uwpapps"></a>
- **Otázka: Návody vytváření programových testů uživatelského rozhraní pro aplikace Univerzální platforma Windows (UWP)?**

   Odpověď **: v**závislosti na platformě, kde testujete svou aplikaci UWP, vytvořte projekt programového testu uživatelského rozhraní jedním z následujících způsobů:

  - Aplikace UWP běžící na místním počítači se spustí jako aplikace ze Storu. Chcete-li tento test otestovat, je nutné použít šablonu **projektu programového testu uživatelského rozhraní (Windows)** . Chcete-li najít tuto šablonu při vytváření nového projektu, použijte příkaz pro **Windows**, **univerzální** uzel. Nebo přejít na uzel **Windows**, **Windows 8**nebo **Windows** .

  - Aplikace UWP běžící na mobilním zařízení nebo emulátoru se spustí jako aplikace pro telefon. Chcete-li tento test otestovat, musíte použít šablonu projektu programového **testu uživatelského rozhraní (Windows Phone)** . Chcete-li najít tuto šablonu při vytváření nového projektu, použijte příkaz pro **Windows**, **univerzální** uzel. Nebo přejít na uzel **Windows**, **Windows 8** **Windows Phone** .

    Po vytvoření projektu zůstane vytváření testu stejné jako předtím.

- **Otázka: Proč nemůžu změnit kód v souboru UIMap. Designer?**

   Odpověď **: všechny**změny kódu, které provedete v souboru UIMapDesigner.cs, budou přepsány pokaždé, když generujete kód pomocí Tvůrce programového testu uživatelského rozhraní UIMap. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [Nastavení jedinečné vlastnosti automatizace pro ovládací prvky Windows Store pro testování](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)

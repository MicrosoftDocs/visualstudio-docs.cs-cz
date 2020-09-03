---
title: Testování aplikací pro Windows UWP a 8,1 pro telefony pomocí programových testů uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f2ac13b62dcc522626fde92b1b29cac9873edec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301830"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Testování aplikací pro UPW a aplikací pro Windows Phone 8.1 pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod použijte pro vytváření testů uživatelského rozhraní pro aplikace UWP, které běží na mobilních zařízeních, emulátorech a aplikacích pro telefon 8,1 založených na jazyce XAML.

## <a name="create-a-simple-windows-phone-app"></a>Vytvoření jednoduché aplikace Windows Phone

1. Vytvořte nový projekt pro prázdnou Windows Phone aplikaci pomocí šablony Visual C# nebo Visual Basic.

     ![Vytvoření nové aplikace Windows Phone](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")

2. V Průzkumník řešení otevřete MainPage. XAML. Z panelu nástrojů přetáhněte ovládací prvek tlačítko a ovládací prvek TextBox na návrhovou plochu.

     ![Přidat contols do souboru MainPage. XAML](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")

3. V okno Vlastnosti název ovládacího prvku tlačítko.

     ![Pojmenování ovládacího prvku tlačítko](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")

4. Pojmenujte ovládací prvek TextBox.

     ![Pojmenování ovládacího prvku TextBox](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")

5. Na návrhové ploše poklikejte na ovládací prvek tlačítko a přidejte následující kód:

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

6. Stisknutím klávesy F5 spusťte aplikaci Windows Phone v emulátoru a ověřte, že funguje.

     ![Spuštění aplikace Windows Phone](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")

7. Ukončete emulátor.

## <a name="deploy-the-windows-phone-app"></a>Nasazení aplikace Windows Phone

1. Předtím, než může programový test uživatelského rozhraní mapovat ovládací prvky aplikace, je nutné aplikaci nasadit.

     ![Nasazení aplikace Windows Phone](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")

     Spustí se emulátor. Aplikace je nyní k dispozici pro testování.

     ![Aplikace nasazená na emulátoru](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")

     Při vytváření kódovaného testu uživatelského rozhraní nechejte emulátor spuštěný.

## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Vytvoření programového testu uživatelského rozhraní pro aplikaci Windows Phone

[Návody vytvořit programové testy uživatelského rozhraní pro aplikace Univerzální platforma Windows (UWP)?](#uwpapps)

1. Přidejte nový projekt programového testu uživatelského rozhraní do řešení pomocí aplikace Windows Phone.

    ![Vytvořit nový programový test uživatelského rozhraní pro Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")

2. Vyberte, chcete-li upravit mapu uživatelského rozhraní pomocí nástroje křížového vlasování.

    ![Vygenerujte programový test uživatelského rozhraní pomocí nástroje pro křížové&#45;vlasy.](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")

3. K výběru aplikace použijte nástroj pro křížové vlasy a potom zkopírujte hodnotu vlastnosti **AutomationId** aplikace, která se použije později ke spuštění aplikace v testu.

    ![Zkopírování hodnoty AutomationId aplikace](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")

4. V emulátoru spusťte aplikaci a pomocí nástroje křížového vlasce vyberte ovládací prvek tlačítko. Pak přidejte ovládací prvek tlačítko do mapování ovládacího prvku uživatelského rozhraní.

    ![Mapování ovládacích prvků pomocí nástroje pro křížovou&#45;vlasů](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")

5. Chcete-li přidat ovládací prvek TextBox do mapování ovládacích prvků uživatelského rozhraní, opakujte předchozí krok.

    ![Použití nástroje pro zaměřovací vlas-&#45;a mapového ovládacího prvku TextBox](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")

6. Vygeneruje kód pro vytvoření kódu pro změny mapování ovládacího prvku uživatelského rozhraní.

    ![Generovat kód z Tvůrce](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")

7. Pomocí nástroje pro křížové vlasy vyberte ovládací prvek TextBox a potom vyberte vlastnost **text** .

    ![Vyberte vlastnost text](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")

8. Přidat kontrolní výraz. V testu bude použit k ověření, zda je hodnota správná.

    ![Přidat kontrolní výraz do testu](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")

9. Přidejte a vygenerujte kód pro metodu assert.

     ![Generovat kód pro kontrolní výraz](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")

10. **Vizuál C #**

     V Průzkumník řešení otevřete soubor UIMap.Designer.cs, abyste zobrazili kód, který jste právě přidali pro metodu Assert a ovládací prvky.

     **Visual Basic**

     V Průzkumník řešení otevřete soubor CodedUITest1. vb. V kódu testovací metody CodedUITestMethod1 () klikněte pravým tlačítkem myši na volání metody assertion, která byla automaticky přidána, `Me.UIMap.AssertMethod1()` a vyberte možnost **Přejít k definici**. Tím se otevře soubor UIMap. Designer. vb v editoru kódu, abyste mohli zobrazit kód, který jste přidali pro metodu Assert a ovládací prvky.

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
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Ovládací prvky**

    ```csharp
    #region Properties
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues
    {
        get
        {
            if ((this.mAssertMethod1ExpectedValues == null))
            {
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();
            }
            return this.mAssertMethod1ExpectedValues;
        }
    }

    public UIApp1Window UIApp1Window
    {
        get
        {
            if ((this.mUIApp1Window == null))
            {
                this.mUIApp1Window = new UIApp1Window();
            }
            return this.mUIApp1Window;
        }
    }
    #endregion

    #region Fields
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;

    private UIApp1Window mUIApp1Window;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
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

11. V Průzkumník řešení otevřete soubor CodedUITest1.cs nebo CodedUITest1. vb. Nyní můžete přidat kód do metody CodedUTTestMethod1 pro akce potřebné ke spuštění testu. K přidání kódu použijte ovládací prvky, které byly přidány do UIMap:

    1. Spusťte aplikaci Windows Phone pomocí vlastnosti Automation ID, kterou jste zkopírovali do schránky dříve:

       ```csharp
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

       ```vb
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

    2. Přidejte gesto klepnutím na ovládací prvek tlačítko:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)
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
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '
            ' Launch the app.
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

## <a name="run-the-coded-ui-test"></a>Spuštění kódovaného testu uživatelského rozhraní

1. Sestavte test a potom spusťte test pomocí Průzkumníka testů.

     ![Sestavení a spuštění testu pomocí Průzkumníka testů](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")

     Spustí se aplikace Windows Phone, akce klepnutí na tlačítko se dokončí a vlastnost text textového pole se vyplní a ověří pomocí metody Assert.

     ![Běh Winodws Phone test](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")

     Po dokončení testu Průzkumník testů potvrdí, že test proběhl úspěšně.

     ![Výsledky Průzkumníka testů](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")

## <a name="use-data-driven-coded-ui-tests-on-windows-phone-apps"></a><a name="TestingPhoneAppsCodedUI_DataDriven"></a> Použití programových testů uživatelského rozhraní řízených daty v aplikacích Windows Phone
 Pro testování různých podmínek lze programový test uživatelského rozhraní spustit vícekrát s různými sadami dat.

 Programové testy UI založené na datech pro Windows Phone jsou definovány pomocí atributu DataRow v testovací metodě. V následujícím příkladu x a y používají hodnoty 1 a 2 pro první iteraci a-1 a-2 pro druhou iteraci testu.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>Otázka: musím v emulátoru nasadit aplikaci Windows Phone, aby bylo možné mapovat ovládací prvky uživatelského rozhraní?
 Odpověď **: Ano**, Tvůrce programového testu uživatelského rozhraní vyžaduje spuštění emulátoru a nasazení aplikace do něj. V opačném případě se zobrazí chybová zpráva oznamující, že se nenašel žádný spuštěný emulátor.

### <a name="q-can-tests-be-executed-on-the-emulator-only-or-can-i-also-use-a-physical-device"></a><a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> Otázka: lze provádět testy pouze v emulátoru, nebo je možné také použít fyzické zařízení?
 Odpověď: je podporována jedna **z**možností. Cíl pro spuštění testu je vybrán změnou typu emulátoru nebo výběrem možnosti zařízení na panelu nástrojů zařízení. Pokud je vybrané zařízení, musí být mobilní zařízení připojené k jednomu z portů USB počítače.

 ![Vyberte verzi emulátoru nebo zařízení physcial.](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Otázka: Proč se mi nezobrazuje možnost zaznamenat programový test uživatelského rozhraní v dialogovém okně generovat kód pro programový test UI?
 Odpověď **: možnost**záznamu není u Windows Phonech aplikací podporována.

### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>Otázka: mohu vytvořit programový test uživatelského rozhraní pro moje aplikace Windows Phone na základě WinJS, Silverlightu nebo HTML5?
 Odpověď: Ne, podporují se jenom aplikace **založené na XAML**.

### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Otázka: mohu vytvořit programové testy uživatelského rozhraní pro moje aplikace Windows Phone v systému, který neběží Windows 8.1 nebo Windows 10?
 Odpověď **: ne**, šablony projektu programového testu uživatelského rozhraní jsou k dispozici pouze na Windows 8.1 a Windows 10. Abyste mohli vytvářet aplikace automatizace pro Univerzální platforma Windows (UWP), budete potřebovat Windows 10.

<a name="uwpapps"></a>
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>Otázka: Návody vytváření programových testů uživatelského rozhraní pro aplikace Univerzální platforma Windows (UWP)?
 Odpověď **: v**závislosti na platformě, kde testujete svou aplikaci UWP, vytvořte projekt programového testu uživatelského rozhraní jedním z následujících způsobů:

- Aplikace UWP běžící na místním počítači se spustí jako aplikace ze Storu. Chcete-li tento test otestovat, je nutné použít šablonu **projektu programového testu uživatelského rozhraní (Windows)** . Chcete-li najít tuto šablonu při vytváření nového projektu, použijte příkaz pro **Windows**, **univerzální** uzel. Nebo přejít na uzel **Windows**, **Windows 8**nebo **Windows** .

- Aplikace UWP běžící na mobilním zařízení nebo emulátoru se spustí jako aplikace pro telefon. Chcete-li tento test otestovat, musíte použít šablonu projektu programového **testu uživatelského rozhraní (Windows Phone)** . Chcete-li najít tuto šablonu při vytváření nového projektu, použijte příkaz pro **Windows**, **univerzální** uzel. Nebo přejít na uzel **Windows**, **Windows 8** **Windows Phone** .

  Po vytvoření projektu zůstane vytváření testu stejné jako předtím.

### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>Otázka: mohu vybrat ovládací prvky, které jsou mimo emulátor?
 Odpověď **: ne**, tvůrce je nerozpozná.

### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>Otázka: mohu použít Tvůrce programového testu UI k mapování ovládacích prvků pomocí fyzického telefonního zařízení?
 Odpověď **: ne**, tvůrce může mapovat prvky uživatelského rozhraní pouze v případě, že vaše aplikace byla nasazena do emulátoru.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nemůžu změnit kód v souboru UIMap. Designer?
 Odpověď **: všechny**změny kódu, které provedete v souboru UIMapDesigner.cs, budou přepsány pokaždé, když generujete kód pomocí Tvůrce programového testu uživatelského rozhraní UIMap. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.

### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>Otázka: mohu na příkazovém řádku spustit programový test uživatelského rozhraní v aplikaci Windows Phone?
 Odpověď **: Ano**, použijete soubor runsettings k určení cílového zařízení pro spuštění testu. Příklad:

 **vstest.console.exe "pathToYourCodedUITestDll"/Settings: devicetarget. runsettings**

 Vzorový soubor runsettings:

```
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
<MSPhoneTest>
<!--to specify test execution on device, use a TargetDevice option as follows-->
<TargetDevice>Device</TargetDevice>
<!--to specify an emulator instead, use a TargetDevice option like below-->
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->
</MSPhoneTest>
</RunSettings>
```

### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>Otázka: Jaké jsou rozdíly mezi programovým testem uživatelského rozhraní pro aplikace Windows Store a aplikace Windows Phone založené na kódování XAML?
 Odpověď **: jedná**se o některé z klíčových rozdílů:

|Příznak|Aplikace pro Windows Store|Aplikace Windows Phone|
|-------------|------------------------|------------------------|
|Cíl pro spuštěné testy|Místní nebo vzdálený počítač. Vzdálené počítače lze zadat při použití automatizovaného testovacího případu pro spuštění testů. Viz [Automatizace testovacího případu v Microsoft Test Manager](https://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Emulátor nebo zařízení. Viz, [Q: lze provádět testy pouze v emulátoru, nebo je možné použít také fyzické zařízení?](#TestingPhoneAppsCodedUI_EmulatorDevice) v tomto tématu.|
|Spustit z příkazového řádku|Soubor nastavení není pro určení cíle vyžadován.|Pro určení cíle se vyžaduje soubor runsettings.|
|Specializované třídy pro ovládací prvky prostředí|[DirectUIControl](/previous-versions/dn248208(v=vs.140))|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|
|Ovládací prvek WebView v aplikaci XAML|Podporováno, pokud používáte specializované třídy HTML * pro interakci s prvky jazyka HTML. Viz třída <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Nepodporováno|
|Spouštění automatizovaných testů z MTM|Podporuje se.|Nepodporováno|
|Testy řízené daty|Informace o použití externích zdrojů dat a použití atributu DataSource pro testovací metodu naleznete v tématu [testy řízené daty](../test/creating-a-data-driven-coded-ui-test.md) .|Data jsou zadána jako vložená pomocí atributu DataRow v testovací metodě. Viz [použití programových testů uživatelského rozhraní řízených daty v aplikacích Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) v tomto tématu.|

## <a name="external-resources"></a>Externí zdroje
 Microsoft Visual Studio blog správy životního cyklu aplikací: [použití kódovaného uživatelského rozhraní k testování aplikací Windows Phone založených na jazyce XAML](https://devblogs.microsoft.com/devops/using-coded-ui-to-test-xaml-based-windows-phone-apps/#comments)

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)

---
title: Testování Windows UWP a aplikací pro Phone 8.1 pomocí programových testů uživatelského rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: gewarren
manager: douge
ms.openlocfilehash: 808482fdd7599adb270fe7634d61d4b88acb0d80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890139"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Testování aplikací pro UPW a aplikací pro Windows Phone 8.1 pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí tohoto průvodce použijte k vytvoření testů uživatelského rozhraní pro aplikace UWP, které běží na mobilním zařízení nebo emulátorů a aplikace založené na XAML Phone 8.1.   
  
## <a name="create-a-simple-windows-phone-app"></a>Vytvoření jednoduché aplikace pro Windows Phone  
  
1.  Vytvořte nový projekt pro prázdnou aplikaci pro Windows Phone pomocí šablony Visual C# nebo Visual Basic.  
  
     ![Vytvoření nové aplikace pro Windows Phone](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")  
  
2.  V Průzkumníku řešení otevřete MainPage.xaml. Z panelu nástrojů přetáhněte ovládací prvek button a ovládací prvek textbox na návrhovou plochu.  
  
     ![Do MainPage.xaml přidejte ovládací](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")  
  
3.  V okně Vlastnosti název ovládacího prvku tlačítko.  
  
     ![Pojmenujte ovládací prvek tlačítko](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")  
  
4.  Název ovládacího prvku textbox.  
  
     ![Název ovládacího prvku textbox](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")  
  
5.  Na návrhové ploše poklikejte na ovládací prvek tlačítka a přidejte následující kód:  
  
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
  
6.  Stisknutím klávesy F5 spusťte aplikaci Windows Phone v emulátoru a ověřte, že je funkční.  
  
     ![Spustit Windows Phone app](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")  
  
7.  Ukončete emulátoru.  
  
## <a name="deploy-the-windows-phone-app"></a>Nasazení Windows Phone app  
  
1.  Než programového testu UI lze mapovat ovládací prvky vaší aplikace, budete muset tuto aplikaci nasadit.  
  
     ![Nasazení Windows Phone app](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")  
  
     Spuštění emulátoru. Aplikace je nyní k dispozici pro testování.  
  
     ![Aplikace nasadit na emulátor](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")  
  
     Zachovejte emulátoru při vytvoření programového testu UI.  
  
## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Vytvoření programového testu UI pro aplikace Windows Phone  

[Jak vytvořit kódované testy uživatelského rozhraní pro aplikace univerzální platformy Windows (UPW)?](#uwpapps)
  
1. Přidáte nový projekt programového testu UI k řešení s aplikací pro Windows Phone.  
  
    ![Vytvořte nový kódovaný test uživatelského rozhraní pro Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")  
  
2. Zvolte upravit mapování uživatelského rozhraní pomocí nástroje vlasového kříže.  
  
    ![Vygenerování programového uživatelského rozhraní testu pomocí křížové&#45;vlasy nástroj. ](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")  
  
3. Pomocí nástroje nitkového kříže vyberte aplikaci, a potom zkopírujte hodnotu pro aplikace **AutomationId** vlastnost, která se později použijí ke spuštění aplikace v testu.  
  
    ![Zkopírujte hodnotu AutomationId aplikace](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")  
  
4. V emulátoru spusťte aplikaci a pomocí nástroje nitkového kříže vyberte ovládací prvek tlačítko. Pak přidejte ovládací prvek tlačítko v mapování ovládacího prvku uživatelského rozhraní.  
  
    ![Použít různé&#45;nástroje kříž ovládací prvky mapy](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")  
  
5. Přidání ovládacího prvku textového pole do mapování ovládacích prvků uživatelského rozhraní, opakujte předchozí krok.  
  
    ![Použít různé&#45;ovládacího prvku textbox vlasů nástroj a mapy](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")  
  
6. Generovat kód pro vytvoření kódu pro změny mapování ovládacího prvku uživatelského rozhraní.  
  
    ![Generování kódu z Tvůrce](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")  
  
7. Pomocí nástroje nitkového kříže vyberte ovládací prvek textového pole a pak vyberte **Text** vlastnost.  
  
    ![Vyberte vlastnost Text](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")  
  
8. Přidáte kontrolní výraz. Použije v testu k ověření, že hodnota je správná.  
  
    ![Přidat kontrolní výraz testu](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")  
  
9. Přidejte a generujte kód pro metodu assert.  
  
     ![Generování kódu pro výraz](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")  
  
10. **Visual C#**  
  
     V Průzkumníku řešení otevřete soubor UIMap.Designer.cs pro zobrazení kódu, který jste právě přidali pro metodu assert a ovládací prvky.  
  
     **Visual Basic**  
  
     V Průzkumníku řešení otevřete soubor CodedUITest1.vb. V CodedUITestMethod1() kódu metody testování, klikněte pravým tlačítkem na volání výrazu metody, které bylo automaticky přidáno `Me.UIMap.AssertMethod1()` a zvolte **přejít k definici**. Tím otevřete soubor UIMap.Designer.vb v editoru kódu, můžete zobrazit kód, který jste přidali pro metodu assert a ovládací prvky.  
  
    > [!WARNING]
    >  Přímo neupravujte soubor UIMap.designer.cs ani UIMap.Designer.vb. Pokud to uděláte, změny do souboru budou přepsány pokaždé, když je generován test.  
  
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
  
11. V Průzkumníku řešení otevřete soubor CodedUITest1.cs nebo CodedUITest1.vb. Nyní můžete přidat kód do metody codeduttestmethod1 pro akce potřebné ke spuštění testu. Pomocí ovládacích prvků, které byly přidány do mapy UIMap přidání kódu:  
  
    1. Spusťte aplikaci Windows Phone pomocí vlastnosti ID automatizace, který jste zkopírovali do schránky dříve:  
  
       ```csharp  
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
       ```vb  
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
    2. Přidejte gesto pro klepnutí na ovládací prvek tlačítka:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
       ```  
  
    3. Ověřte, že volání metody assert, která byla automaticky vygenerována, přichází po spuštění aplikace a klepněte na gesto na tlačítku:  
  
       ```csharp  
       this.UIMap.AssertMethod1();  
       ```  
  
       ```vb  
       Me.UIMap.AssertMethod1()  
       ```  
  
       Po přidání kódu by měla testovací metoda CodedUITestMethod1 vypadat takto:  
  
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
  
## <a name="run-the-coded-ui-test"></a>Spustit programový test uživatelského rozhraní  
  
1.  Sestavte test a poté jej spusťte pomocí Průzkumníka testů.  
  
     ![Sestavení a spuštění testů pomocí Průzkumníku testů](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")  
  
     Spuštění aplikace Windows Phone, akce klepnutí na tlačítka po dokončení a Text textovém poli vlastnosti je vyplněný a ověřené pomocí metody assert.  
  
     ![Spouštění testů produktu Windows Phone](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")  
  
     Po dokončení testu, Průzkumník testů potvrzuje, že test proběhl úspěšně.  
  
     ![Výsledky Průzkumníka testů](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")  
  
##  <a name="TestingPhoneAppsCodedUI_DataDriven"></a> Použití s daty kódované testy uživatelského rozhraní pro aplikace z Windows Phone  
 K testování různých podmínek, programový test UI lze spustit několikrát s různými sadami dat.  
  
 S daty programové testy uživatelského rozhraní pro Windows Phone jsou definovány pomocí atributu DataRow v testovací metodě. V následujícím příkladu, x a y pomocí hodnoty 1 a 2 pro první iterace a -1 -2 pro druhý iteraci tohoto testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
## <a name="q--a"></a>Dotazy a odpovědi  
  
### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>Otázka: mám k nasazení aplikace pro Windows Phone v emulátoru účely mapování ovládacích prvků uživatelského rozhraní?  
 **A**: Ano, Tvůrce programového testu uživatelského rozhraní vyžaduje, aby emulátor používat, a do zařízení nasadit aplikaci. V opačném případě vyvolá chybová zpráva s oznámením, že nebyly nalezeny žádné běžící emulátor.  
  
###  <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> Dotaz: lze testy spustit v emulátoru pouze nebo můžu také použít fyzické zařízení?  
 **A**: jednu z možností je podporována. Cíl pro spuštění testu se vybírá změnou typu emulátor nebo výběru zařízení na panelu nástrojů zařízení. Pokud je vybrané zařízení, telefonní modré zařízení musí být připojené k některé z portu USB počítače.  
  
 ![Vyberte verzi emulátoru nebo fyzická zařízení](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")  
  
### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Otázka: Proč nevidím možnost zaznamenat Moje programový test uživatelského rozhraní v generování kódu pro dialogové okno programový Test uživatelského rozhraní?  
 **A**: pro aplikace Windows Phone není podporována možnost záznamu.  
  
### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>Dotaz: lze vytvořit kódovaný test uživatelského rozhraní pro mé aplikace Windows Phone založené na WinJS, Silverlight nebo HTML5?  
 **A**: Ne, jsou podporovány pouze XAML na základě aplikace.  
  
### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Dotaz: lze vytvořit kódované testy uživatelského rozhraní pro mé aplikace Windows Phone v systému, na kterém neběží Windows 8.1 nebo Windows 10?  
 **A**: Ne, šablon projekt programového testu uživatelského rozhraní jsou dostupné jenom pro Windows 8.1 a Windows 10. Pokud chcete vytvořit automatizace pro aplikace univerzální platformy Windows (UPW), budete potřebovat Windows 10.  

<a name="uwpapps"></a>  
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>Otázka: Jak vytvořím programové testy uživatelského rozhraní pro aplikace univerzální platformy Windows (UPW)  
 **A**: v závislosti na platformě, kde testování vaší aplikace pro UPW, vytvořte projekt programového testu uživatelského rozhraní v jednom z těchto způsobů:  
  
- Aplikace pro UPW spuštěné na místním počítači se spustí jako Store app. Abyste to mohli otestovat, je nutné použít **projekt programového uživatelského rozhraní testu (Windows)** šablony. Vyhledejte tuto šablonu, když vytvoříte nový projekt, přejděte **Windows**, **univerzální** uzlu. Nebo můžete přejít na **Windows**, **Windows 8**, **Windows** uzlu.  
  
- Aplikace pro UPW běžící na mobilním zařízení nebo emulátoru se spustí jako aplikaci pro telefon. Abyste to mohli otestovat, je nutné použít **projekt programového uživatelského rozhraní testu (Windows Phone)** šablony. Vyhledejte tuto šablonu, když vytvoříte nový projekt, přejděte **Windows**, **univerzální** uzlu. Nebo můžete přejít na **Windows**, **Windows 8**, **Windows Phone** uzlu.  
  
  Po vytvoření projektu pro vytváření testu zůstává stejná jako předtím.  
  
### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>Dotaz: lze vybrat ovládací prvky, které jsou mimo emulátor?  
 **A**: Ne, Tvůrce nebude rozpoznat.  
  
### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>Otázka: Mohu použít Tvůrce programového testu uživatelského rozhraní pro mapování ovládacích prvků pomocí fyzických telefon?  
 **A**: Ne, Tvůrce mapují prvky uživatelského rozhraní Pokud vaše aplikace byla nasazena do emulátoru.  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nelze upravit kód v souboru UIMap.Designer?  
 **A**: žádné změny kódu v souboru UIMapDesigner.cs bude přepsán při každém vytvoření kódu pomocí UIMap – Tvůrce programového testu uživatelského rozhraní. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.  
  
### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>Dotaz: lze spustit programový test UI v aplikaci Windows Phone z příkazového řádku?  
 **A**: Ano, určete cílovému zařízení pro provádění testů pomocí souboru runsettings. Příklad:  
  
 **vstest.Console.exe "pathToYourCodedUITestDll" /settings:devicetarget.runsettings**  
  
 Ukázkový soubor runsettings:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
<MSPhoneTest>  
<!--to specify test execution on device, use a TargetDevice option as follows-->  
<TargetDevice>Device</TargetDevice>  
<!--to specify an emulator instead, use a TargetDevice option like below-->  
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->  
</MSPhoneTest>  
</RunSettings>  
```  
  
### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>Otázka: jaké jsou rozdíly mezi programové testy uživatelského rozhraní pro aplikace Windows Store založených na XAML a aplikací Windows Phone?  
 **A**: Toto jsou některé hlavní rozdíly:  
  
|Funkce|Aplikace pro Windows Store|Aplikace Windows Phone|  
|-------------|------------------------|------------------------|  
|Cíl pro spouštění testů|Místním nebo vzdáleném počítači. Vzdálené počítače je možné zadat při spuštění testů pomocí automatizovaného testového případu. Zobrazit [automatizovaný testovací proces v nástroji Microsoft Test Manager](http://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Emulátor nebo zařízení. Zobrazit, [dotaz: lze testy spouštět v emulátoru pouze nebo můžu také použít fyzické zařízení?](#TestingPhoneAppsCodedUI_EmulatorDevice) v tomto tématu.|  
|Spusťte z příkazového řádku|Není nutné určit cílový soubor s nastavením.|Chcete-li zadat cíl je vyžadován soubor Runsettings.|  
|Specializované třídy pro ovládací prvky prostředí|<xref:Microsoft.VisualStudio.TestTools.UITesting.DirectUIControls.DirectUIControl>|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|  
|Ovládací prvek WebView v aplikace v jazyce XAML|Podporováno, pokud použijete Html * specializované třídy pro interakci s prvky jazyka HTML. Viz <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Není podporováno.|  
|Spuštění automatizovaných testů z nástroje MTM|Podporované.|Není podporováno.|  
|Testy řízené daty|Zobrazit [daty řízené testy](../test/creating-a-data-driven-coded-ui-test.md) informace o používání externí zdroje dat a zdroj dat atribut v testovací metodě.|Data jsou zadány jako vložené, pomocí atributu DataRow v testovací metodě. Zobrazit [řízené daty pomocí programových testů UI pro aplikace z Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) v tomto tématu.|  
  
## <a name="external-resources"></a>Externí zdroje  
 Blog Microsoft Visual Studio Application Lifecycle Management: [pomocí programového uživatelského rozhraní k testování aplikací pro Windows Phone založené na XAML](http://blogs.msdn.com/b/visualstudioalm/archive/2014/04/05/using-coded-ui-to-test-xaml-based-windows-phone-apps.aspx?PageIndex=2#comments)  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)




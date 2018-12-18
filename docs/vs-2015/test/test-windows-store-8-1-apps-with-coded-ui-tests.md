---
title: Testování aplikace 8.1 Store a Windows UWP pomocí programových testů uživatelského rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: gewarren
manager: douge
ms.openlocfilehash: 70973305764319ecb8ebf902945c92eb4723af7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934298"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Testování aplikace 8.1 Store a Windows UWP pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí tohoto průvodce použijte k vytvoření testů uživatelského rozhraní pro aplikace UWP a aplikací založených na XAML Store 8.1.
  
## <a name="create-a-simple-windows-store-app"></a>Vytvoření jednoduché aplikace pro Windows Store  
  
1.  Pokud chcete spustit programové testy UI pro aplikace pro Windows Store založených na XAML, je nutné [nastavit jedinečnou vlastnost automatizace, který identifikuje každý ovládací prvek](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Na **nástroje** nabídky, přejděte k **možnosti** a klikněte na tlačítko **textový Editor**, pak **XAML**a nakonec **různé** .  
  
     Zaškrtněte políčko pro automaticky pojmenovat interaktivní prvky při vytvoření.  
  
     ![XAML různé možnosti](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
2.  Vytvořte nový projekt pro prázdnou XAML na základě aplikace pro Windows Store pomocí šablony Visual C# nebo Visual Basic.  
  
     ![Vytvořit prázdnou aplikaci pro Windows Store &#40;XAML&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  V Průzkumníku řešení otevřete MainPage.xaml. Z panelu nástrojů přetáhněte ovládací prvek button a ovládací prvek textbox na návrhovou plochu.  
  
     ![Navrhujte aplikace Windows Store](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Poklepejte na ovládací prvek tlačítko a přidejte následující kód:  
  
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
  
5.  Stisknutím klávesy F5 spusťte aplikaci Windows Store.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Vytvoření a spuštění programového testu UI pro aplikace Windows Store  

[Jak vytvořit kódované testy uživatelského rozhraní pro aplikace univerzální platformy Windows (UPW)?](#uwpapps)
  
1. Vytvořte nový projekt programového testu UI pro aplikace Windows Store.  
  
    ![Nový projekt programového uživatelského rozhraní tét &#40;Windows Store Apps&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")  
  
2. Zvolte upravit mapování uživatelského rozhraní pomocí nástroje vlasového kříže.  
  
    ![Zvolte upravit mapování uživatelského rozhraní nebo přidat kontrolní výrazy](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3. Pomocí Tvůrce programového testu uživatelského rozhraní nástroje vlasového kříže vyberte dlaždici aplikace, klikněte pravým tlačítkem na **AutomationId** a zvolte **Kopírovat hodnotu do schránky**. Hodnota ve schránce se použije později pro zápis akce ke spuštění aplikace pro testování.  
  
    ![Kopírovat do schránky AutomationId](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4. Ve spuštěné aplikaci Windows Store použijte nástroj nitkového kříže vyberte ovládací prvek button a ovládací prvek textového pole. Po přidání každého ovládacího prvku, zvolte **přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní** tlačítko na panelu nástrojů Tvůrce programového testu UI.  
  
    ![Přidat ovládací prvek do mapy uživatelského rozhraní](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5. Zvolte **generovat kód** tlačítko na panelu nástrojů Tvůrce programového testu uživatelského rozhraní a klikněte na tlačítko **generovat** vytvořit kód pro změny mapování ovládacího prvku uživatelského rozhraní.  
  
    ![Generování kódu pro mapování uživatelského rozhraní](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")  
  
6. Klikněte na tlačítko pro nastavení hodnoty do textového pole.  
  
    ![Klikněte na tlačítko Nastavit hodnotu pole textbox](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7. Pomocí nástroje nitkového kříže vyberte ovládací prvek textového pole a pak vyberte **Text** vlastnost.  
  
    ![Vyberte vlastnost Text](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8. Přidáte kontrolní výraz. Použije v testu k ověření, že hodnota je správná.  
  
    ![Zvolte testbox s křížové&#45;vlasy a přidat kontrolní výraz](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Přidejte a generujte kód pro kontrolní výraz.  
  
     ![Generovat kód pro textové pole kontrolního výrazu](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     V Průzkumníku řešení otevřete soubor UIMap.Designer.cs pro zobrazení přidaného kódu pro metodu assert a ovládací prvky.  
  
     **Visual Basic**  
  
     V Průzkumníku řešení otevřete soubor CodedUITest1.vb a v testovací metody codeduitestmethod1(), klikněte pravým tlačítkem na volání výrazu metody, které bylo automaticky přidáno `Me.UIMap.AssertMethod1()` a zvolte **přejít k definici**. Tím otevřete soubor UIMap.Designer.vb v editoru kódu, můžete zobrazit zobrazení přidaného kódu pro metodu assert a ovládací prvky.  
  
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
  
11. V Průzkumníku řešení otevřete soubor CodedUITest1.cs nebo CodedUITest1.vb. Nyní můžete přidat kód do metody codeduttestmethod1 pro akce nezbytné ke spuštění testu pomocí ovládacích prvků přidaných do UIMap:  
  
    1. Spusťte aplikaci Windows Store pomocí vlastnosti ID automatizace, který jste zkopírovali do schránky dříve:  
  
       ```csharp  
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
       ```  
  
       ```vb  
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
       ```  
  
    2. Přidejte gesto pro klepnutí na ovládací prvek tlačítka:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
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
  
12. Sestavte test a poté jej spusťte pomocí Průzkumníka testů.  
  
     ![Spustit programového testu uživatelského rozhraní pomocí Průzkumníku testů](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Spuštění aplikace Windows Store, akce klepnutí na tlačítka po dokončení a Text textovém poli vlastnosti je vyplněný a ověřené pomocí metody assert.  
  
     ![Spuštění programového testu UI](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")  
  
     Po dokončení testu v Průzkumníku testů uvedeno, že test proběhl úspěšně.  
  
     ![Předaný testu zobrazí v Průzkumníku testů](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Dotazy a odpovědi  
  
-   **Otázka: Proč nevidím možnost zaznamenat Moje programový test uživatelského rozhraní v generování kódu pro dialogové okno programový Test uživatelského rozhraní?**  
  
     **A**: pro aplikace Windows Store není podporována možnost záznamu.  
  
-   **Dotaz: lze vytvořit kódovaný test uživatelského rozhraní pro mé aplikace Windows Store založené na WinJS?**  
  
     **A**: Ne, jsou podporovány pouze XAML na základě aplikace.  
  
-   **Dotaz: lze vytvořit kódované testy uživatelského rozhraní pro mé aplikace Windows Store v systému, na kterém neběží Windows 8.1 nebo Windows 10?**  
  
     **A**: Ne, šablon projekt programového testu uživatelského rozhraní jsou dostupné jenom pro Windows 8.1 a Windows 10. Pokud chcete vytvořit automatizace pro aplikace univerzální platformy Windows (UPW), budete potřebovat Windows 10.  

<a name="uwpapps"></a>
- **Otázka: Jak vytvořím programové testy uživatelského rozhraní pro aplikace univerzální platformy Windows (UPW)**  
  
   **A**: v závislosti na platformě, kde testování vaší aplikace pro UPW, vytvořte projekt programového testu uživatelského rozhraní v jednom z těchto způsobů:  
  
  - Aplikace pro UPW spuštěné na místním počítači se spustí jako Store app. Abyste to mohli otestovat, je nutné použít **projekt programového uživatelského rozhraní testu (Windows)** šablony. Vyhledejte tuto šablonu, když vytvoříte nový projekt, přejděte **Windows**, **univerzální** uzlu. Nebo můžete přejít na **Windows**, **Windows 8**, **Windows** uzlu.  
  
  - Aplikace pro UPW běžící na mobilním zařízení nebo emulátoru se spustí jako aplikaci pro telefon. Abyste to mohli otestovat, je nutné použít **projekt programového uživatelského rozhraní testu (Windows Phone)** šablony. Vyhledejte tuto šablonu, když vytvoříte nový projekt, přejděte **Windows**, **univerzální** uzlu. Nebo můžete přejít na **Windows**, **Windows 8**, **Windows Phone** uzlu.  
  
    Po vytvoření projektu pro vytváření testu zůstává stejná jako předtím.  
  
- **Otázka: Proč nelze upravit kód v souboru UIMap.Designer?**  
  
   **A**: žádné změny kódu v souboru UIMapDesigner.cs bude přepsán při každém vytvoření kódu pomocí UIMap – Tvůrce programového testu uživatelského rozhraní. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Nastavení jedinečné vlastnosti automatizace pro ovládací prvky pro Windows Store za účelem testování](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)




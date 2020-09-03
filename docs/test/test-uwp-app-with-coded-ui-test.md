---
title: Testování aplikace pro UWP pomocí programového testu uživatelského rozhraní
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: aad17d244d70051a363a4cde294c592968093ba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286749"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Vytvoření programového testu uživatelského rozhraní pro otestování aplikace pro UWP

Tento článek vysvětluje, jak vytvořit programový test uživatelského rozhraní pro aplikaci Univerzální platforma Windows (UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Vytvoření aplikace pro UWP k otestování

Prvním krokem je vytvoření jednoduché aplikace pro UWP, na které se má test spustit.

1. V aplikaci Visual Studio vytvořte nový projekt pomocí šablony **prázdná aplikace (univerzální pro Windows)** pro Visual C# nebo Visual Basic.

   ::: moniker range="vs-2017"

   ![Prázdná šablona pro univerzální aplikaci pro Windows](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. V dialogovém okně **Nový projekt Univerzální platforma Windows** vyberte **OK** , aby se přijímaly výchozí verze platformy.

1. Z **Průzkumník řešení**otevřete *MainPage. XAML*.

   Soubor se otevře v **Návrhář XAML**.

1. Přetáhněte ovládací prvek tlačítko a ovládací prvek TextBox ze **sady nástrojů** na návrhovou plochu.

     ![Návrh aplikace pro UWP](../test/media/toolbox-controls.png)

1. Zadejte názvy ovládacích prvků. Vyberte ovládací prvek TextBox a potom v okně **vlastnosti** zadejte do pole **název** text **TextBox** . Vyberte ovládací prvek tlačítko a potom v okně **vlastnosti** zadejte do pole **název** **tlačítko** .

1. Dvakrát klikněte na ovládací prvek tlačítko a do těla metody přidejte následující kód `Button_Click` . Tento kód jednoduše nastaví text v textovém poli na název ovládacího prvku tlačítko, stačí, když nám dáte něco pro ověření pomocí kódovaného testu uživatelského rozhraní, vytvoříme ho později.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Spusťte aplikaci stisknutím klávesy **CTRL** + **F5** . Mělo by se zobrazit něco podobného:

   ![Aplikace UWP s tlačítkem a textovým polem](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Vytvoření programového testu uživatelského rozhraní

1. Chcete-li do řešení přidat testovací projekt, klikněte pravým tlačítkem na řešení v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **Nový projekt**.

1. Vyhledejte a vyberte šablonu **projektu programového testu uživatelského rozhraní (Universal Windows)** .

   ::: moniker range="vs-2017"

   ![Nový projekt programového testu UI](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Pokud nevidíte šablonu **projektu programového testu UI (Universal Windows)** , je nutné [nainstalovat komponentu programového testu uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. V dialogovém okně **generovat kód pro programový test uživatelského rozhraní** vyberte možnost **ručně upravit test**.

   ![Vygeneruje kód pro dialog programového testu uživatelského rozhraní.](../test/media/manually-edit-the-test.png)

1. Pokud vaše aplikace UWP ještě není spuštěná, spusťte ji stisknutím **klávesy CTRL** + **F5**.

1. Otevřete dialogové okno Tvůrce programového **testu uživatelského rozhraní** tak, že umístíte kurzor do `CodedUITestMethod1` metody a pak zvolíte **test**  >  **generovat kód pro programový test UI**  >  **použít Tvůrce programového testu uživatelského rozhraní**.

1. Přidejte ovládací prvky do mapování ovládacího prvku uživatelského rozhraní. Pomocí nástroje **Tvůrce programového testu UI** pro křížové ovládání vyberte ovládací prvek tlačítko v aplikaci UWP. V dialogovém okně **Přidat kontrolní výrazy** rozbalte v případě potřeby podokno **Mapa ovládacího prvku uživatelského rozhraní** a pak vyberte **Přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.

     ![Přidat ovládací prvek do mapy uživatelského rozhraní](../test/media/add-control-to-ui-control-map.png)

1. Zopakováním předchozího kroku přidejte ovládací prvek TextBox do mapování ovládacího prvku uživatelského rozhraní.

1. V dialogovém okně Tvůrce programového **testu UI** vyberte **vytvořit kód** nebo stiskněte **kombinaci kláves CTRL +** + **G**. Pak vyberte **vytvořit** a vytvořte kód pro změny mapování ovládacího prvku uživatelského rozhraní.

     ![Vygenerovat kód pro mapu uživatelského rozhraní](../test/media/generate-code-dialog.png)

1. Chcete-li ověřit, zda se text v textovém poli změní na **tlačítko** po kliknutí na tlačítko, klikněte na tlačítko.

     ![Pro nastavení hodnoty TextBox klikněte na tlačítko ovládací prvek tlačítko](../test/media/uwp-app-button-textbox.png)

1. Přidejte kontrolní výraz pro ověření textu v ovládacím prvku TextBox. Pomocí nástroje pro křížové vlasy vyberte ovládací prvek TextBox a potom v dialogovém okně **Přidat kontrolní výrazy** vyberte vlastnost **text** . Pak vyberte **Přidat kontrolní výraz** nebo stiskněte klávesu **ALT** + **a**. V poli **Zpráva o selhání kontrolního výrazu** zadejte **hodnotu textové pole není očekáváno.** a pak vyberte **OK**.

     ![Zvolit textové pole s křížovým vlasy a přidat kontrolní výraz](../test/media/add-assertion-for-text.png)

1. Vygenerujte zkušební kód pro kontrolní výraz. V dialogovém okně Tvůrce programového **testu UI** vyberte **generovat kód**. V dialogovém okně **generovat kód** vyberte **Přidat a generovat**.

     ![Vygenerovat kód pro kontrolní výraz TextBox](../test/media/add-and-generate-assert-method.png)

   V **Průzkumník řešení**otevřete *UIMap.Designer.cs* a zobrazte přidaný kód pro metodu Assert a ovládací prvky.

   > [!TIP]
   > Pokud používáte Visual Basic, otevřete *CodedUITest1. vb*. Poté v `CodedUITestMethod1()` kódu metody testu klikněte pravým tlačítkem myši na volání metody Assert `Me.UIMap.AssertMethod1()` a zvolte možnost **Přejít k definici**. *UIMap. Designer. vb* se otevře v editoru kódu a můžete zobrazit přidaný kód pro metodu Assert a ovládací prvky.

    > [!WARNING]
    > Neupravujte soubory *UIMap.Designer.cs* nebo *UIMap. Designer. vb* přímo. Pokud to uděláte, změny budou při vygenerování testu přepsány.

    Metoda Assert vypadá takto:

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

1. Dál musíme získat **AutomationId** [aplikace](#create-a-uwp-app-to-test) pro UWP, kterou chceme testovat. Otevřete nabídku **Start** systému Windows, abyste viděli dlaždici aplikace. Pak přetáhněte ikonu cíle nástroje pro křížové vlasy ![ ](media/target-icon.png) z dialogového okna Tvůrce programového **testu UI** na dlaždici pro vaši aplikaci. Až se modrý rámeček kolem dlaždice dopustí, uvolněte myš.

   ![Nástroj pro křížové vlasy](media/cross-hair-tool.png)

   Otevře se dialogové okno **Přidat kontrolní výrazy** a zobrazí **AutomationId** pro vaši aplikaci. Klikněte pravým tlačítkem na **AutomationId** a vyberte **Kopírovat hodnotu do schránky**.

   ![AutomationID v dialogovém okně Přidat kontrolní výraz](../test/media/automation-id.png)

1. Přidejte kód do testovací metody pro spuštění aplikace UWP. V **Průzkumník řešení**otevřete *CodedUITest1.cs* nebo *CodedUITest1. vb*. Nad rámec volání `AssertMethod1` přidejte kód pro spuštění aplikace UWP:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   V ukázkovém kódu nahraďte ID Automation hodnotou, kterou jste zkopírovali do schránky v předchozím kroku.

   > [!IMPORTANT]
   > Ořízne začátek ID automatizace a odebere znaky, jako je například **P ~**. Pokud tyto znaky neoříznete, test vyvolá `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` při pokusu o spuštění aplikace.

1. Potom do testovací metody přidejte kód pro kliknutí na tlačítko. Na řádku po `XamlWindow.Launch` přidejte gesto klepnutím na ovládací prvek tlačítko:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po přidání kódu by se měla provést úplná `CodedUITestMethod1` testovací metoda, jak je znázorněno níže:

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

1. Sestavte projekt testů a pak otevřete **Průzkumník testů** výběrem **test**  >  **Windows**  >  **Průzkumník testů**systému Windows.

1. Kliknutím na **Spustit vše** spusťte test.

   Aplikace se otevře, tlačítko se otevře a vlastnost **text textového** pole se naplní. Metoda Assert ověří vlastnost **text** v textovém poli.

   Po dokončení testu **Průzkumník testů** zobrazí, že test proběhl úspěšně.

   ![Úspěšná zobrazení testů v Průzkumníku testů](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Otázka: Proč se mi nezobrazuje možnost zaznamenat programový test uživatelského rozhraní v dialogovém okně generovat kód pro programový test UI?

Odpověď **: možnost**nahrávání není pro aplikace pro UWP podporována.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Otázka: mohu vytvořit programový test uživatelského rozhraní pro moje aplikace UWP založené na WinJS?

Odpověď: Ne, jsou podporovány pouze aplikace **založené na jazyce**XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nemůžu změnit kód v souboru UIMap. Designer?

Odpověď **: všechny**změny kódu, které provedete v souboru *UIMapDesigner.cs* , budou přepsány pokaždé, když generujete kód pomocí Tvůrce programového **testu uživatelského rozhraní**. Pokud je nutné změnit zaznamenanou metodu, zkopírujte ji do souboru *UIMap.cs* a přejmenujte ji. Soubor *UIMap.cs* lze použít k přepsání metod a vlastností v souboru *UIMapDesigner.cs* . Odeberte odkaz na původní metodu v souboru *CodedUITest.cs* a nahraďte ji názvem metody, kterou jste přejmenovali.

## <a name="see-also"></a>Viz také

- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Nastavení jedinečných vlastností automatizace pro ovládací prvky UWP](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)

---
title: Testování aplikace UPW s kódovým testem ui
ms.date: 05/31/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: fdd3d98bd848bb6fe679809a58f2e316a316f012
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590355"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Vytvoření kódovaného testu ui pro testování aplikace UPW

Tento článek vysvětluje, jak vytvořit kódovaný test ui pro univerzální platformu Windows (UPW).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Vytvoření aplikace UPW k testování

Prvním krokem je vytvoření jednoduché aplikace UPW pro spuštění testu.

1. V sadě Visual Studio vytvořte nový projekt pomocí šablony **Blank App (Universal Windows)** pro Visual C# nebo Visual Basic.

   ::: moniker range="vs-2017"

   ![Prázdná univerzální šablona aplikace pro Windows](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. V dialogovém **okně Nový projekt univerzální platformy Windows** vyberte **ok,** chcete-li přijmout výchozí verze platformy.

1. V **Průzkumníku řešení**otevřete *soubor MainPage.xaml*.

   Soubor se otevře v **Návrháři XAML**.

1. Přetáhněte ovládací prvek tlačítka a ovládací prvek textového pole z **panelu nástrojů** na návrhovou plochu.

     ![Návrh aplikace UPW](../test/media/toolbox-controls.png)

1. Pojmenujte ovládací prvky. Vyberte ovládací prvek textového pole a v okně **Vlastnosti** zadejte **textové pole** do pole **Název.** Vyberte ovládací prvek tlačítka a pak v okně **Vlastnosti** zadejte **tlačítko** do pole **Název.**

1. Poklepejte na ovládací prvek tlačítka a přidejte `Button_Click` následující kód do těla metody. Tento kód jednoduše nastaví text v textovém poli na název ovládacího prvku tlačítka, jen aby nám něco ověřit s kódované houfnice test vytvoříme později.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Stisknutím **klávesy Ctrl**+**F5** aplikaci spusťte. Mělo by se zobrazit něco podobného:

   ![Aplikace UPW s tlačítkem a textovým polem](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Vytvoření kódovaného testu ui

1. Chcete-li do řešení přidat testovací projekt, klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a zvolte **Přidat** > **nový projekt**.

1. Vyhledejte a vyberte šablonu **Coded UI Test Project (Universal Windows).**

   ::: moniker range="vs-2017"

   ![Nový kódovaný testovací projekt ui](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Pokud šablonu **Coded UI Test Project (Universal Windows)** nevidíte, je třeba [nainstalovat kódovku testovací součást uživatelského prostředí](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. V dialogovém **okně Generovat kód pro kódovaný test ui** vyberte Ručně upravit **test**.

   ![Generovat kód pro kódovaný dialog testu ui](../test/media/manually-edit-the-test.png)

1. Pokud aplikace UPW ještě není spuštěná, spusťte ji stisknutím **klávesctrl**+**f5**.

1. Otevřete dialogové okno Tvůrce testovaného kódu `CodedUITestMethod1` **umítavého** nastavení umístěním kurzoru do metody a výběrem **možnosti Testovat** > **generovaný kód pro programový test použití** > **ui programovaného tvůrce testů ui**.

1. Přidejte ovládací prvky do mapy ovládacího prvku ui. Pomocí **nástroje pro křížový kříž Tvůrce kódovaného ui** pro výběr vyberte ovládací prvek tlačítka v aplikaci UPW. V dialogovém okně **Přidat kontrolní výrazy** rozbalte v případě potřeby podokno **Mapy ovládacího prvku ui** a pak vyberte **Přidat ovládací prvek do mapy ovládacího prvku ui**.

     ![Přidání ovládacího prvku do mapy ui](../test/media/add-control-to-ui-control-map.png)

1. Opakováním předchozího kroku přidejte ovládací prvek textového pole do mapy ovládacího prvku ui.

1. V dialogovém okně **Coded UI Test Builder** vyberte **Generovat kód** nebo stiskněte **Ctrl**+**G**. Pak vyberte **Generovat,** chcete-li vytvořit kód pro změny mapy ovládacího prvku ui.

     ![Generovat kód pro mapu uj.](../test/media/generate-code-dialog.png)

1. Chcete-li ověřit, zda se text v textovém poli při klepnutí na tlačítko změní na **tlačítko,** klepněte na tlačítko.

     ![Chcete-li nastavit hodnotu textového pole, klepněte na ovládací prvek tlačítka.](../test/media/uwp-app-button-textbox.png)

1. Přidejte kontrolní výraz pro ověření textu v ovládacím prvku textového pole. Pomocí nástroje nitkového kříže vyberte ovládací prvek textového pole a pak vyberte vlastnost **Text** v dialogovém okně **Přidat kontrolní výrazy.** Potom vyberte **Přidat kontrolní výraz** nebo stiskněte **Alt**+**A**. Do pole **Zpráva o selhání kontrolního výrazu** je hodnota **textového pole neočekávaná.** a pak vyberte **OK**.

     ![Volba textového pole s nitkovým křížem a přidání kontrolního výrazu](../test/media/add-assertion-for-text.png)

1. Vygenerujte testovací kód pro kontrolní výraz. V dialogovém okně **Tvůrce testů programového u.i.** vyberte **generovat kód**. V dialogovém okně **Generovat kód** vyberte Přidat **a generovat**.

     ![Generovat kód pro kontrolní výraz textového pole](../test/media/add-and-generate-assert-method.png)

   V **Průzkumníku řešení** *otevřete UIMap.Designer.cs* a zobrazte přidaný kód metody assert a ovládacích prvků.

   > [!TIP]
   > Pokud používáte visual basic, otevřete *CodedUITest1.vb*. Potom v `CodedUITestMethod1()` kódu testovací metody klikněte pravým tlačítkem `Me.UIMap.AssertMethod1()` myši na volání metody assert a zvolte **Přejít na definici**. *UIMap.Designer.vb* otevře v editoru kódu a můžete zobrazit přidaný kód pro assert metody a ovládací prvky.

    > [!WARNING]
    > Soubory *UIMap.designer.cs* nebo *UIMap.Designer.vb* neupravujte přímo. Pokud tak učiníte, změny budou přepsány při generování testu.

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

1. Dále potřebujeme získat **AutomationId** [aplikace](#create-a-uwp-app-to-test) UPW, které chceme otestovat. Otevřete nabídku **Start** systému Windows a podívejte se na dlaždici aplikace. Potom přetáhněte ikonu ![](media/target-icon.png) zaměřovací ho nástroje Cíl z dialogového okna **Coded UI Test Builder** na dlaždici aplikace. Když dlaždice obklopuje modrý rámeček, uvolněte myš.

   ![Nástroj pro nitkový vlas](media/cross-hair-tool.png)

   Otevře se dialogové okno **Přidat kontrolní výrazy** a zobrazí **automationid** pro vaši aplikaci. Klepněte pravým tlačítkem myši na **automationId** a zvolte **Kopírovat hodnotu do schránky**.

   ![AutomationID v dialogovém okně Přidat kontrolní výraz](../test/media/automation-id.png)

1. Přidejte kód do testovací metody pro spuštění aplikace UPW. V **Průzkumníku řešení**otevřete *CodedUITest1.cs* nebo *CodedUITest1.vb*. Nad voláním `AssertMethod1`přidejte kód pro spuštění aplikace UPW:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Nahraďte ID automatizace v ukázkovém kódu hodnotou, kterou jste zkopírovali do schránky v předchozím kroku.

   > [!IMPORTANT]
   > Ořízněte začátek ID automatizace, abyste odstranili znaky, například **P~**. Pokud tyto znaky neoříznete, `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` test vyvolá při pokusu o spuštění aplikace.

1. Dále přidejte kód do testovací metody a klikněte na tlačítko. Na řádku `XamlWindow.Launch`za , přidejte gesto pro klepnutí na ovládací prvek tlačítka:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po přidání kódu by `CodedUITestMethod1` měla být úplná zkušební metoda zobrazena takto:

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

1. Vytvořte testovací projekt a spusťte **Průzkumníka testů** výběrem **možnosti Test** > **Windows** > Test**Explorer**.

1. Chcete-li spustit test, vyberte možnost **Spustit vše.**

   Aplikace se otevře, tlačítko je poklepané a textbox **je text** ovázaná. Metoda assert ověřuje vlastnost **Text** textového pole.

   Po dokončení testu **Průzkumník testů** zobrazí, že test prošel.

   ![Předané testovací displeje v Průzkumníku testů](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Otázka: Proč nevidím možnost zaznamenat kódovaný test ui v dialogovém okně Generovat kód pro programový test ui?

**A**: Možnost záznamu není podporována pro aplikace UPW.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Otázka: Mohu vytvořit kódovaný test ui pro mé aplikace UPW na základě WinJS?

**A**: Ne, jsou podporovány pouze aplikace založené na XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Otázka: Proč nelze upravit kód v souboru UIMap.Designer?

**A**: Všechny změny kódu, které provedete v *souboru UIMapDesigner.cs,* jsou přepsány při každém generování kódu pomocí **tvůrce programového testu ui**. Pokud máte upravit nahranou metodu, zkopírujte ji do *UIMap.cs* souboru a přejmenujte ji. Soubor *UIMap.cs* lze použít k přepsání metod a vlastností v *souboru UIMapDesigner.cs.* Odeberte odkaz na původní metodu v *souboru CodedUITest.cs* a nahraďte ji přejmenovaným názvem metody.

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Nastavení jedinečných vlastností automatizace pro ovládací prvky UPW](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)

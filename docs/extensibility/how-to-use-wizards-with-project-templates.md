---
title: 'Postupy: Použití průvodců se šablonami projektů'
description: Naučte se používat rozhraní IWizard v sadě Visual Studio SDK, které umožňuje spustit vlastní kód, když uživatel vytvoří projekt ze šablony.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41290f946c198ed854cad9a7eb2af088f6fe228a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082280"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Postupy: použití průvodců se šablonami projektů

Visual Studio poskytuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní, které při implementaci umožňuje spustit vlastní kód, když uživatel vytvoří projekt ze šablony.

Přizpůsobení šablony projektu lze použít k zobrazení vlastního uživatelského rozhraní, které shromažďuje vstup uživatele pro přizpůsobení šablony, přidání dalších souborů do šablony nebo jakékoli jiné akce povolené v projektu.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Metody rozhraní jsou volány v různých časech během vytváření projektu, od okamžiku, kdy uživatel klikne na **tlačítko OK** v dialogovém okně **Nový projekt** . Každá metoda rozhraní je pojmenována k popisu bodu, ve kterém je volána. Například Visual Studio volá <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> okamžitě při zahájení vytváření projektu, takže je vhodné místo pro zápis vlastního kódu ke shromáždění uživatelského vstupu.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Vytvoření projektu šablony projektu s projektem VSIX

Začněte vytvářet vlastní šablonu pomocí projektu projektové šablony, který je součástí sady Visual Studio SDK. V tomto postupu použijeme projekt šablony projektu C#, ale existuje i Visual Basic projekt šablony projektu. Pak přidáte projekt VSIX do řešení, které obsahuje projekt šablony projektu.

1. Vytvořte projekt šablony projektu C# (v aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt** a vyhledejte "šablona projektu"). Pojmenujte ho **MyProjectTemplate**.

   > [!NOTE]
   > Může se zobrazit výzva k instalaci sady Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Přidejte nový projekt VSIX do stejného řešení jako projekt šablony projektu (v **Průzkumník řešení** vyberte uzel řešení, klikněte pravým tlačítkem myši a vyberte **Přidat**  >  **Nový projekt** a vyhledejte "VSIX"). Pojmenujte ho **MyProjectWizard.**

3. Nastavte projekt VSIX jako spouštěný projekt. V **Průzkumník řešení** vyberte uzel projekt VSIX, klikněte pravým tlačítkem myši a vyberte **nastavit jako spouštěný projekt**.

4. Přidejte projekt šablony jako Asset projektu VSIX. V **Průzkumník řešení** v uzlu projektu VSIX Najděte soubor *source. extension. vsixmanifest* . Poklikejte na ni a otevře se v editoru manifestu.

5. V editoru manifestu vyberte kartu **assety** na levé straně okna.

6. Na kartě **assets (prostředky** ) vyberte možnost **Nový**. V okně **Přidat nový prostředek** pro pole Typ vyberte **Microsoft. VisualStudio. ProjectTemplate**. V poli **zdroj** vyberte **projekt v aktuálním řešení**. V poli **projekt** vyberte **MyProjectTemplate**. Pak klikněte na **OK**.

7. Sestavte řešení a spusťte ladění. Zobrazí se druhá instance aplikace Visual Studio. (Může to trvat několik minut.)

8. Ve druhé instanci aplikace Visual Studio se pokuste vytvořit nový projekt s novou šablonou (**soubor**  >  **Nový**  >  **projekt**, vyhledejte "MyProject"). Nový projekt by se měl zobrazit s třídou s názvem **Class1**. Nyní jste vytvořili vlastní šablonu projektu. Zastavte ladění hned teď.

## <a name="create-a-custom-template-wizard"></a>Průvodce vytvořením vlastní šablony

Tento postup ukazuje, jak vytvořit vlastního průvodce, který otevře formulář Windows před vytvořením projektu. Formulář umožňuje uživatelům přidat vlastní hodnotu parametru, která je přidána ke zdrojovému kódu během vytváření projektu.

1. Nastavte projekt VSIX, aby mohl vytvořit sestavení.

2. V **Průzkumník řešení** vyberte uzel projekt VSIX. Pod **Průzkumník řešení** byste měli vidět okno **vlastnosti** . Pokud to neuděláte, vyberte **Zobrazit**  >  **okno Vlastnosti** nebo stiskněte **F4**. V okně **vlastnosti** vyberte následující pole pro `true` :

   - **Zahrnout sestavení do kontejneru VSIX**

   - **Zahrnout symboly ladění do kontejneru VSIX**

   - **Zahrnout symboly ladění do místního nasazení VSIX**

3. Přidejte sestavení jako prostředek do projektu VSIX. Otevřete soubor *source. extension. vsixmanifest* a vyberte kartu **assety** . V okně **Přidat nový prostředek** pro **typ** vyberte **Microsoft. VisualStudio. Assembly**, pro **zdroj** vyberte **projekt v aktuálním řešení** a pro **projekt** vyberte **MyProjectWizard**.

4. Do projektu VSIX přidejte následující odkazy. (V **Průzkumník řešení** pod uzlem projekt VSIX vyberte **odkazy**, klikněte pravým tlačítkem myši a vyberte **Přidat odkaz**.) V dialogovém okně **Přidat odkaz** na kartě **rozhraní** najděte sestavení **System. model Windows Forms** a vyberte ho. Také vyhledejte a vyberte sestavení **System** a **System. Drawing** . Nyní vyberte kartu **rozšíření** . Vyhledejte sestavení **EnvDTE** a vyberte ho. Vyhledejte také sestavení **Microsoft. VisualStudio. TemplateWizardInterface** a vyberte ho. Klikněte na **OK**.

5. Přidejte třídu pro implementaci průvodce do projektu VSIX. (V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu VSIX a vyberte **Přidat**, **Nová položka** a pak **Třída**.) Pojmenujte třídu **WizardImplementation**.

6. Nahraďte kód v souboru *WizardImplementationClass. cs* následujícím kódem:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    **UserInputForm** , na který se odkazuje v tomto kódu, se implementuje později.

    `WizardImplementation`Třída obsahuje implementace metod pro každého člena <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . V tomto příkladu pouze <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda provede úlohu. Všechny ostatní metody buď nedělají nic, nebo nevrátí `true` .

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>Metoda přijímá čtyři parametry:

   - <xref:System.Object>Parametr, který lze přetypovat na kořenový <xref:EnvDTE._DTE> objekt, aby bylo možné projekt přizpůsobit.

   - <xref:System.Collections.Generic.Dictionary%602>Parametr, který obsahuje kolekci všech předem definovaných parametrů v šabloně. Další informace o parametrech šablony najdete v tématu [parametry šablony](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Parametr, který obsahuje informace o tom, jaký druh šablony se používá.

   - <xref:System.Object>Pole, které obsahuje sadu parametrů předaných průvodci sadou Visual Studio.

     Tento příklad přidá hodnotu parametru z formuláře vstupu uživatele do <xref:System.Collections.Generic.Dictionary%602> parametru. Každá instance `$custommessage$` parametru v projektu bude nahrazena textem zadaným uživatelem.

7. Nyní vytvořte **UserInputForm**. V souboru *WizardImplementation. cs* přidejte následující kód za konec `WizardImplementation` třídy.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Formulář vstupu uživatele poskytuje jednoduchou formu pro zadání vlastního parametru. Formulář obsahuje textové pole s názvem `textBox1` a tlačítko s názvem `button1` . Po kliknutí na tlačítko je text z textového pole uložen v `customMessage` parametru.

## <a name="connect-the-wizard-to-the-custom-template"></a>Připojit průvodce k vlastní šabloně

Chcete-li, aby vaše vlastní šablona projektu používala vlastního průvodce, je nutné podepsat sestavení průvodce a přidat některé řádky do vlastní šablony projektu, aby věděl, kde najít implementaci Průvodce při vytvoření nového projektu.

1. Podepište sestavení. V **Průzkumník řešení** vyberte projekt VSIX, klikněte pravým tlačítkem a vyberte **Vlastnosti projektu**.

2. V okně **Vlastnosti projektu** vyberte kartu **podepisování** . na kartě **podepisování** zaškrtněte možnost **podepsat sestavení**. V poli **Vyberte soubor klíče se silným názvem** vyberte **\<New>** . V okně **vytvořit klíč se silným názvem** zadejte do pole **klíč názvu souboru** **Key. snk**. Zrušte kontrolu **souboru chránit můj klíč pomocí pole heslo** .

3. V **Průzkumník řešení** vyberte projekt VSIX a vyhledejte okno **vlastnosti** .

4. Nastavte pole **Kopírovat výstup sestavení do výstupního adresáře** na **hodnotu true**. To umožňuje zkopírovat sestavení do výstupního adresáře, když je řešení znovu sestaveno. Stále je obsažen v `.vsix` souboru. Aby bylo možné zjistit podpisový klíč, je nutné zobrazit sestavení.

5. Znovu sestavte řešení.

6. Nyní můžete najít soubor Key. snk v adresáři projektu MyProjectWizard (*\<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*). Zkopírujte soubor *Key. snk* .

7. Přejít do výstupního adresáře a vyhledat sestavení (*\<your disk location> \ MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Sem vložte soubor *Key. snk* . (Tato akce není nezbytně nutná, ale provede následující kroky.)

8. Otevřete příkazové okno a přejděte do adresáře, ve kterém bylo sestavení vytvořeno.

9. Vyhledejte nástroj pro podepisování *sn.exe* . Například v operačním systému Windows 10 64 může být typická cesta následující:

     *C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Pokud nástroj nemůžete najít, zkuste v příkazovém okně Spustit příkaz **/r. sn.exe** . Zaznamenejte si cestu.

10. Extrahujte veřejný klíč ze souboru *Key. snk* . V příkazovém okně zadejte

     **\<location of sn.exe>\sn.exe-p Key. snk – soubor.**

     Nezapomeňte zadat cestu *sn.exe* s uvozovkami, pokud jsou v názvech adresářů nějaké mezery.

11. Získání tokenu veřejného klíče ze souboru.

     **\<location of sn.exe>\sn.exe-t soubor. Key.**

     Znovu Nezapomeňte zadat uvozovky. Měl by se zobrazit řádek ve výstupu, jako je to

     **Token veřejného klíče je \<token>**

     Tuto hodnotu si poznamenejte.

12. Do souboru *. vstemplate* šablony projektu přidejte odkaz na vlastního průvodce. V **Průzkumník řešení** vyhledejte soubor s názvem *MyProjectTemplate. vstemplate* a otevřete ho. Za konec \<TemplateContent> oddílu přidejte následující část:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Kde **MyProjectWizard** je název sestavení a **token** je token, který jste zkopírovali v předchozím kroku.

13. Uložte všechny soubory v projektu a znovu sestavte.

## <a name="add-the-custom-parameter-to-the-template"></a>Přidat vlastní parametr do šablony

V tomto příkladu se v projektu, který se používá jako šablona, zobrazí zpráva zadaná ve formuláři vstupu uživatele vlastního průvodce.

1. V **Průzkumník řešení** přejdete do projektu **MyProjectTemplate** a otevřete *Class1. cs*.

2. V `Main` metodě aplikace přidejte následující řádek kódu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametr `$custommessage$` je nahrazen textem zadaným ve formuláři vstupu uživatele při vytvoření projektu ze šablony.

Zde je úplný soubor s kódem předtím, než byl exportován do šablony.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Použití vlastního průvodce

Nyní můžete vytvořit projekt ze šablony a použít vlastního průvodce.

1. Znovu sestavte řešení a spusťte ladění. Měla by se zobrazit druhá instance aplikace Visual Studio.

2. Vytvořte nový projekt MyProjectTemplate. (**Soubor**  >  **Nové**  >  **Projekt**).

3. V dialogovém okně **Nový projekt** vyhledejte pomocí příkazu "MyProject" šablonu, zadejte název a klikněte na tlačítko **OK**.

     Otevře se formulář průvodce vstupu uživatele.

4. Zadejte hodnotu pro vlastní parametr a klikněte na tlačítko.

     Formulář průvodce vstupu uživatele se zavře a vytvoří se projekt ze šablony.

5. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor zdrojového kódu a klikněte na **Zobrazit kód**.

     Všimněte si, že byl `$custommessage$` nahrazen textem zadaným ve formuláři průvodce vstupu uživatele.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [WizardExtension – – element (šablony sady Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)

---
title: 'Postupy: Použití průvodců se šablonami projektů'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710537"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Postup: Použití průvodců se šablonami projektů

Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> poskytuje rozhraní, které při implementaci umožňuje spustit vlastní kód, když uživatel vytvoří projekt ze šablony.

Přizpůsobení šablony projektu lze použít k zobrazení vlastního uživatelského rozhraní, které shromažďuje uživatelský vstup pro přizpůsobení šablony, přidání dalších souborů do šablony nebo jakoukoli jinou akci povolenou v projektu.

Metody <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní jsou volány v různých časech při vytváření projektu, počínaje, jakmile uživatel klepne na **tlačítko OK** v dialogovém okně **Nový projekt.** Každá metoda rozhraní je pojmenována k popisu bodu, ve kterém je volána. Například Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> volá okamžitě při zahájení vytváření projektu, takže je vhodné místo pro zápis vlastního kódu pro shromažďování vstupu uživatele.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Vytvoření projektu šablony projektu pomocí projektu VSIX

Začnete vytvářet vlastní šablonu s projektem šablony projektu, který je součástí sady Visual Studio SDK. V tomto postupu použijeme projekt šablony projektu jazyka C#, ale je také projekt šablony projektu jazyka Visual Basic. Potom přidáte projekt VSIX do řešení, které obsahuje projekt šablony projektu.

1. Vytvořte projekt šablony projektu jazyka C# (v sadě Visual Studio vyberte **Soubor** > **nový** > **projekt** a vyhledejte "šablonu projektu"). Pojmenujte ji **MyProjectTemplate**.

   > [!NOTE]
   > Můžete být vyzváni k instalaci sady Visual Studio SDK. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Přidejte nový projekt VSIX ve stejném řešení jako projekt šablony projektu (v **Průzkumníku řešení**vyberte uzel řešení, klikněte pravým tlačítkem myši a vyberte **Přidat** > **nový projekt** a vyhledejte "vsix"). Pojmenujte jej **MyProjectWizard.**

3. Nastavte projekt VSIX jako projekt spuštění. V **Průzkumníku řešení**vyberte uzel projektu VSIX, klepněte pravým tlačítkem myši a vyberte **nastavit jako spouštěcí projekt**.

4. Přidejte projekt šablony jako datový zdroj projektu VSIX. V **Průzkumníku řešení**najděte v uzlu projektu VSIX soubor *source.extension.vsixmanifest.* Poklepáním ji otevřete v editoru manifestu.

5. V editoru manifestu vyberte kartu **Datové zdroje** na levé straně okna.

6. Na kartě **Datové zdroje** vyberte **Nový**. V okně **Přidat nový datový zdroj** vyberte pro pole Typ šablonu **Microsoft.VisualStudio.ProjectTemplate**. V poli **Zdroj** vyberte **možnost A projekt v aktuálním řešení**. V poli **Projekt** vyberte **MyProjectTemplate**. Pak klikněte na **OK**.

7. Sestavte řešení a začněte ladit. Zobrazí se druhá instance sady Visual Studio. (To může trvat několik minut.)

8. Ve druhé instanci sady Visual Studio zkuste vytvořit nový projekt s novou šablonou **(Soubor** > **nový** > **projekt**, vyhledejte "myproject"). Nový projekt by se měl zobrazit s třídou s názvem **Class1**. Nyní jste vytvořili vlastní šablonu projektu! Přestaňte ladit.

## <a name="create-a-custom-template-wizard"></a>Vytvoření průvodce vlastní šablonou

Tento postup ukazuje, jak vytvořit vlastního průvodce, který otevře formulář systému Windows před vytvořením projektu. Formulář umožňuje uživatelům přidat vlastní hodnotu parametru, která je přidána do zdrojového kódu během vytváření projektu.

1. Nastavte projekt VSIX tak, aby mohl vytvořit sestavení.

2. V **Průzkumníku řešení**vyberte uzel projektu VSIX. V části **Průzkumník řešení**byste měli vidět okno **Vlastnosti.** Pokud tak neučiníte, vyberte **zobrazit** > **okno vlastností**nebo stiskněte **klávesu F4**. V okně **Vlastnosti** vyberte `true`následující pole, která chcete :

   - **Zahrnout sestavení do kontejneru VSIX**

   - **Zahrnout symboly ladění do kontejneru VSIX**

   - **Zahrnout symboly ladění do místního nasazení VSIX**

3. Přidejte sestavení jako datový zdroj do projektu VSIX. Otevřete soubor *source.extension.vsixmanifest* a vyberte kartu **Datové zdroje.** V okně **Přidat nový datový zdroj** vyberte pro **typ** **Microsoft.VisualStudio.Assembly položku Microsoft.VisualStudio.Assembly**, pro **položku Zdroj** **vyberte projekt v aktuálním řešení**a pro **project** **vyberte MyProjectWizard**.

4. Přidejte následující odkazy na projekt VSIX. (V **Průzkumníku řešení**vyberte v uzlu projektu VSIX **položku Reference ,** klepněte pravým tlačítkem myši a vyberte přidat **odkaz**.) V dialogovém okně **Přidat odkaz** najděte na kartě **Framework** sestavení **System.Windows Forms** a vyberte ho. Také najít a vybrat **systém** a **System.Drawing** sestavy. Nyní vyberte kartu **Rozšíření.** **EnvDTE** Najděte také sestavení **Microsoft.VisualStudio.TemplateWizardInterface** a vyberte ho. Klikněte na tlačítko **OK**.

5. Přidejte třídu pro implementaci průvodce do projektu VSIX. (V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu VSIX a **vyberte**přidat , potom **na položku New Item**a potom na **položku**.) Pojmenujte třídu **WizardImplementation**.

6. Nahraďte kód v *souboru WizardImplementationClass.cs* následujícím kódem:

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

    **UserInputForm** odkazovaný v tomto kódu bude implementován později.

    Třída `WizardImplementation` obsahuje implementace metod pro <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>každého člena . V tomto příkladu <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> pouze metoda provádí úkol. Všechny ostatní metody buď `true`nedělají nic, nebo vrátit .

    Metoda <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> přijímá čtyři parametry:

   - Parametr, <xref:System.Object> který lze přetypovat na kořenový <xref:EnvDTE._DTE> objekt, který umožňuje přizpůsobit projekt.

   - Parametr, <xref:System.Collections.Generic.Dictionary%602> který obsahuje kolekci všech předdefinovaných parametrů v šabloně. Další informace o parametrech šablony naleznete v [tématu Template parameters](../ide/template-parameters.md).

   - Parametr, <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> který obsahuje informace o tom, jaký druh šablony se používá.

   - Pole, <xref:System.Object> které obsahuje sadu parametrů předaných průvodci visual studio.

     Tento příklad přidá hodnotu parametru z <xref:System.Collections.Generic.Dictionary%602> uživatelského vstupního formuláře do parametru. Každá instance `$custommessage$` parametru v projektu bude nahrazena textem zadaným uživatelem.

7. Nyní vytvořte **UserInputForm**. Do *WizardImplementation.cs* souboru přidejte následující kód `WizardImplementation` za konec třídy.

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

    Uživatelský vstupní formulář poskytuje jednoduchý formulář pro zadání vlastního parametru. Formulář obsahuje textové pole `textBox1` s názvem `button1`a tlačítko s názvem . Po klepnutí na tlačítko je text z textového `customMessage` pole uložen v parametru.

## <a name="connect-the-wizard-to-the-custom-template"></a>Připojení průvodce k vlastní šabloně

Aby vaše vlastní šablona projektu mohla používat vlastní průvodce, musíte podepsat sestavení průvodce a přidat některé řádky do vlastní šablony projektu, abyste věděli, kde najít implementaci průvodce při vytvoření nového projektu.

1. Podepište shromáždění. V **Průzkumníku řešení**vyberte projekt VSIX, klepněte pravým tlačítkem myši a vyberte **vlastnosti projektu**.

2. V okně **Vlastnosti projektu** vyberte kartu **Signing** **Sign the assembly** **Podpis.** V poli **Zvolit silný název souboru klíče** vyberte ** \<Nový>**. V okně **Vytvořit silný klíč názvu** zadejte do pole Název **souboru klíče** příkaz **key.snk**. Zaškrtnutí políčka Chránit soubor klíče pomocí pole **s heslem**

3. V **Průzkumníku řešení**vyberte projekt VSIX a vyhledejte okno **Vlastnosti.**

4. Nastavte pole **Kopírovat výstup sestavení na výstupní adresář** na **hodnotu true**. To umožňuje sestavení zkopírovat do výstupního adresáře při opětovném sestavení řešení. Je stále obsažen a `.vsix` obsažen v souboru. Chcete-li zjistit jeho podpisový klíč, musíte zobrazit sestavení.

5. Znovu sestavte řešení.

6. Nyní můžete najít soubor key.snk v adresáři projektu MyProjectWizard*\<(umístění disku>\MyProjectTemplate\MyProjectWizard\key.snk*). Zkopírujte soubor *key.snk.*

7. Přejděte do výstupního adresáře a vyhledejte sestavení*\<(umístění disku>\MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll).* Sem vložte soubor *key.snk.* (To není nezbytně nutné, ale usnadní to následující kroky.)

8. Otevřete příkazové okno a změňte adresář, ve kterém bylo sestavení vytvořeno.

9. Najděte podpisový nástroj *sn.exe.* Například v 64bitovém operačním systému Windows 10 by typická cesta byla následující:

     *C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Nástroje*

     Pokud nástroj nemůžete najít, zkuste spustit **soubor /R . sn.exe** v příkazovém okně. Poznamenejte si cestu.

10. Extrahujte veřejný klíč ze souboru *key.snk.* V příkazovém okně zadejte

     **\<umístění souboru sn.exe>\sn.exe -p key.snk outfile.key.key.**

     Nezapomeňte obklopit cestu *sn.exe* s uvozovkami, pokud jsou v názvech adresářů mezery!

11. Získejte token veřejného klíče z outfile:

     **\<umístění souboru sn.exe>\sn.exe -t outfile.key.**

     Opět nezapomeňte na uvozovky. Měli byste vidět řádek ve výstupu, jako je tento

     **Token veřejného \<klíče je>tokenu**

     Poznamenejte si tuto hodnotu.

12. Přidejte odkaz na vlastního průvodce do souboru *.vstemplate* šablony projektu. V **Průzkumníku řešení**vyhledejte soubor s názvem *MyProjectTemplate.vstemplate*a otevřete jej. Za konec sekce \<TemplateContent> přidejte následující část:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Kde **MyProjectWizard** je název sestavení a **token** je token, který jste zkopírovali v předchozím kroku.

13. Uložte všechny soubory v projektu a znovu vytvořit.

## <a name="add-the-custom-parameter-to-the-template"></a>Přidání vlastního parametru do šablony

V tomto příkladu projekt použitý jako šablona zobrazí zprávu zadanou ve formuláři pro vstup uživatele vlastního průvodce.

1. V **Průzkumníku řešení**přejděte do projektu **MyProjectTemplate** a otevřete *Class1.cs*.

2. V `Main` metodě aplikace přidejte následující řádek kódu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametr `$custommessage$` je nahrazen textem zadaným ve formuláři pro vstup uživatele při vytvoření projektu ze šablony.

Zde je úplný soubor kódu před jeho exportem do šablony.

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

1. Znovu sestavte řešení a začněte ladit. Měla by se zobrazit druhá instance sady Visual Studio.

2. Vytvořte nový projekt MyProjectTemplate. (**Soubor** > **nový** > **projekt**).

3. V dialogovém okně Nový projekt vyhledejte šablonu v poli **Nový projekt,** zadejte název a klepněte na tlačítko **OK**.

     Otevře se uživatelský vstupní formulář průvodce.

4. Zadejte hodnotu vlastního parametru a klepněte na tlačítko.

     Uživatelský vstupní formulář průvodce se zavře a ze šablony se vytvoří projekt.

5. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor zdrojového kódu a klepněte na příkaz **Zobrazit kód**.

     Všimněte `$custommessage$` si, že byl nahrazen textem zadaným ve vstupním formuláři průvodce uživatelem.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Element WizardExtension (šablony sady Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)

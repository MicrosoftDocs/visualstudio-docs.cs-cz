---
title: 'Postupy: použití průvodců se šablonami projektů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 650b9c360013d06216e607269f77afd24f3cc22c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783750"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Postupy: Použití průvodců se šablonami projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní, pokud je implementována, budete moci spouštět vlastní kód, když uživatel vytvoří projekt ze šablony.  
  
 Přizpůsobení šablony projektu umožňuje zobrazit vlastní uživatelské rozhraní shromažďující vstupem uživatele k přizpůsobení šablony, přidejte další soubory do šablony nebo jakoukoli jinou akci, která je povolená v projektu.  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Metody rozhraní jsou volány v různých časech, zatímco probíhá vytvoření projektu, počínaje tím, jak uživatel klikne **OK** na **nový projekt** dialogové okno. Každá metoda rozhraní je pojmenována k popsání bodu, ve kterém je volána. Například volání sady Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> okamžitě při spuštění pro vytvoření projektu, takže správné umístění pro zápis vlastního kódu ke shromažďování vstupu uživatele.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Vytvoření projektu šablony projektu s projektem VSIX  
 Můžete začít vytvářet vlastní šablonu pomocí projektu šablony projektu., která je součástí sady Visual Studio SDK. V tomto postupu použijeme šablonu projektu projektu C#, ale je také projektu šablony projektů Visual Basic. Potom přidáte projekt VSIX do řešení, které obsahuje projekt šablony projektu.  
  
1.  Vytvoření projektu jazyka C# projekt šablony (v sadě Visual Studio **soubor / nový / Project / Visual C# / rozšiřitelnost / šablona projektu C#**). Pojmenujte ji **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Můžete být vyzváni k instalaci sady Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Přidat nový projekt VSIX (**soubor / nový / Project / Visual C# / rozšiřitelnost / projekt VSIX**) ve stejném řešení jako šablona projektu pro projekt (v **Průzkumníka řešení**, vyberte uzel řešení Klikněte pravým tlačítkem a vyberte **Add / New Project**). Pojmenujte ji **MyProjectWizard.**  
  
3.  Nastavte projekt VSIX jako projekt po spuštění. V **Průzkumníka řešení**, vyberte uzel řešení, klikněte pravým tlačítkem a vyberte **nastavit jako spouštěný projekt**.  
  
4.  Přidáte šablonu projektu jako prostředek projektu VSIX. V **Průzkumníka řešení**, pod uzlem projektu VSIX, vyhledejte **source.extension.vsixmanifest** souboru. Dvojím kliknutím ho otevřete v editoru manifestu.  
  
5.  V editoru manifestu vyberte **prostředky** karty na levé straně okna.  
  
6.  V **prostředky** kartu, vyberte možnost **nový**. V **přidat nové aktivum** okno pro pole typu, vyberte **Microsoft.VisualStudio.ProjectTemplate**. V **zdroj** pole, vyberte **projekt v aktuálním řešení**. V **projektu** pole, vyberte **MyProjectTemplate**. Pak klikněte na tlačítko **OK**.  
  
7.  Sestavte řešení a spusťte ladění. Zobrazí se druhé instanci aplikace Visual Studio. (To může trvat několik minut.)  
  
8.  Ve druhé instanci aplikace Visual Studio pokuste se vytvořit nový projekt s novou šablonu. (**Soubor / nový / Project / Visual C# / MyProject šablony**). Nový projekt by se měla objevit s třídou s názvem **Class1**. Nyní jste vytvořili vlastní šablonu projektu! Nyní Zastavte ladění.  
  
## <a name="creating-a-custom-template-wizard"></a>Vytvoření vlastního průvodce šablony  
 Toto téma ukazuje, jak vytvořit vlastního průvodce, který otevře formulář Windows před vytvořením projektu. Formulář umožňuje uživatelům přidávat vlastní hodnotu parametru, který je přidán ke zdrojovému kódu během vytváření projektu.  
  
1. Nastavení projektu VSIX, aby mělo vytvořit sestavení.  
  
2. V **Průzkumníka řešení**, vyberte uzel projektu VSIX. Níže v Průzkumníku řešení, měli byste vidět **vlastnosti** okna. Pokud ho nevidíte, vyberte **zobrazit / okno vlastností**, nebo stiskněte klávesu **F4**. V okně Vlastnosti vyberte následující pole, která `true`:  
  
   -   **IncludeAssemblyInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3. Přidáte sestavení jako prostředek do projektu VSIX. Otevřete soubor source.extension.vsixmanifest a vyberte **prostředky** kartu. V **přidat nové aktivum** okně pro **typ** vyberte **Microsoft.VisualStudio.Assembly**, pro **zdroj** vyberte **A projekt v aktuálním řešení**a pro **projektu** vyberte **MyTemplateWizard**.  
  
4. Přidejte následující odkazy do projektu VSIX. (V **Průzkumníka řešení**, v části VSIX projekt vyberte uzel **odkazy**, klikněte pravým tlačítkem a vyberte **přidat odkaz**.) V **přidat odkaz** dialogového okna v **Framework** kartu, najdete **System.Windows formuláře** sestavení a vyberte ji. Teď vyberte **rozšíření** najít kartu **EnvDTE** sestavení a vyberte ji. Také najít **Microsoft.VisualStudio.TemplateWizardInterface** sestavení a vyberte ji. Klikněte na tlačítko **OK**.  
  
5. Přidejte třídu pro implementaci průvodce do projektu VSIX. (V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu VSIX a vyberte **přidat**, pak **nová položka**, pak **třídy**.) Název třídy **WizardImplementation**.  
  
6. Nahraďte kód v **WizardImplementationClass.cs** souboru následujícím kódem:  
  
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
  
    **UserInputForm** odkazované v tomto kódu se provede později.  
  
    `WizardImplementation` Třída obsahuje implementace metody pro každého člena <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. V tomto příkladu, pouze <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metoda provede úlohu. Všechny ostatní metody neprovádějí žádnou akci nebo vrátí `true`.  
  
    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda přijímá čtyři parametry:  
  
   - <xref:System.Object> Parametr, který může být převeden do kořenového adresáře <xref:EnvDTE._DTE> objektu, která umožňuje přizpůsobit projekt.  
  
   - A <xref:System.Collections.Generic.Dictionary%602> parametr, který obsahuje kolekci všech předem definovaných parametrů v šabloně. Další informace o parametrech šablon naleznete v tématu [parametry šablony](../ide/template-parameters.md).  
  
   - A <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parametr, který obsahuje informace o jaký druh šablony je používán.  
  
   - <xref:System.Object> Pole, které obsahuje sadu parametrů předaných průvodci pomocí sady Visual Studio.  
  
     V tomto příkladu přidá hodnotu parametru ze vstupního formuláře uživatele do <xref:System.Collections.Generic.Dictionary%602> parametru. Každá instance `$custommessage$` parametr v projektu bude nahrazena textem zadaným uživatelem. Do projektu musíte přidat následující sestavení:  
  
7. Teď vytvořte **UserInputForm**. V **WizardImplementation.cs** přidejte následující kód na konci **WizardImplementation** třídy.  
  
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
           }  
       }  
   ```  
  
    Formulář vstupu uživatele poskytuje jednoduchý formulář pro zadávání vlastního parametru. Formulář obsahuje textové pole s názvem `textBox1` a tlačítko s názvem `button1`. Po kliknutí na tlačítko je text z textového pole uložen v `customMessage` parametru.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Připojení Průvodce pro vlastní šablony  
 Aby vaše vlastní šablonu projektu použít vlastního průvodce musíte podepsat sestavení průvodce a přidat některé řádky do vaší vlastní šablonu projektu umožňuje vědět, kde najít implementaci Průvodce při vytváření nového projektu.  
  
1. Podepište sestavení. V **Průzkumníka řešení**, vyberte projekt VSIX, klikněte pravým tlačítkem a vyberte **vlastnosti projektu**.  
  
2. V **vlastnosti projektu** okna, vyberte **podepisování** kartu v **podepisování** kartě **podepsat sestavení**. V **vyberte soubor klíče se silným názvem** pole, vyberte  **\<nový >**. V **vytvořit klíč se silným názvem** okno v **název souboru klíče** zadejte **klíč.snk**. Zrušte zaškrtnutí políčka **chránit můj soubor klíče s heslem** pole.  
  
3. V **Průzkumníka řešení**, vyberte projekt VSIX a najít **vlastnosti** okna.  
  
4. Nastavte **kopírovat sestavení výstupu do výstupního adresáře** pole **true**. To umožňuje sestavení kopírovat do výstupního adresáře, pokud je znovu sestavit řešení. Stále je obsažena v souboru .vsix. Potřebujete zobrazit sestavení, aby bylo možné zjistit jeho podpisový klíč.  
  
5. Znovu sestavte řešení.  
  
6. Můžete teď najít klíč.snk soubor v adresáři projektu MyProjectWizard (**\<umístění na disku > \MyProjectTemplate\MyProjectWizard\key.snk**). Zkopírujte soubor klíč.snk.  
  
7. Přejděte do výstupního adresáře a najít sestavení (**\<umístění na disku > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Vložte soubor klíč.snk tady. (To není nezbytně nutné, ale to vám usnadní následující kroky.)  
  
8. Otevřete okno příkazového řádku a přejděte do adresáře, ve kterém byla vytvořena sestavení.  
  
9. Najít **sn.exe** nástroj pro podepisování. Například v operačním systému Windows 10 64-bit, typické cesta by být následující:  
  
     **C:\Program soubory (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 nástroje**  
  
     Pokud nemůžete najít nástroj, zkuste spustit **kde/r.  sn.exe** v příkazovém okně. Poznamenejte si cestu.  
  
10. Extrahujte veřejný klíč ze souboru klíč.snk. V příkazovém okně zadejte  
  
     **\<umístění nástroje sn.exe > \sn.exe - p klíč.snk outfile.key.**  
  
     Nezapomeňte před a za cestu sn.exe uvozovek Pokud jsou mezery v názvech adresářů!  
  
11. Získání tokenu veřejného klíče z Výstupní_soubor:  
  
     **\<umístění nástroje sn.exe > \sn.exe - t outfile.key.**  
  
     Nezapomeňte znovu, uvozovky. Měli byste vidět řádku v výstup podobný tomuto  
  
     **Token veřejného klíče je <token>**  
  
     Poznamenejte si tuto hodnotu.  
  
12. K souboru .vstemplate šablony projektu přidejte odkaz na vlastního průvodce. V Průzkumníku řešení najít soubor s názvem MyProjectTemplate.vstemplate a otevřete ho. Po skončení \<TemplateContent > části, přidejte následující části:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Kde **MyProjectWizard** je název sestavení, a **token** je token, který jste zkopírovali v předchozím kroku.  
  
13. Uložte všechny soubory v projektu a znovu sestavte.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Přidání vlastních parametrů do šablony  
 V tomto příkladu projekt použitý jako šablona zobrazí zprávu určenou ve formuláři vstupu uživatele vlastního průvodce.  
  
1. V Průzkumníku řešení, přejděte **MyProjectTemplate** projektu a otevřete **Class1.cs**.  
  
2. V `Main` metoda aplikace, přidejte následující řádek kódu.  
  
   ```  
   Console.WriteLine("$custommessage$");  
   ```  
  
    Parametr `$custommessage$` je nahrazena textem zadaným ve formuláři vstupu uživatele při vytvoření projektu ze šablony.  
  
   Tady je soubor s úplným kódem dříve, než byl exportován do šablony.  
  
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
  
## <a name="using-the-custom-wizard"></a>Použití vlastního průvodce  
 Nyní můžete vytvořit projekt ze šablony a použít vlastního průvodce.  
  
1.  Znovu sestavte řešení a spusťte ladění. Druhou instanci aplikace Visual Studio by se zobrazit.  
  
2.  Vytvoření nového projektu MyProjectTemplate. (**Soubor / nový / Project / Visual C# / MyProjectTemplate**)  
  
3.  V **nový projekt** dialogovém okně nalezněte vaši šablonu, zadejte název a klikněte na tlačítko **OK**.  
  
     Otevře se formulář průvodce vstupu uživatele.  
  
4.  Zadejte hodnotu pro vlastní parametr a klikněte na tlačítko.  
  
     Formulář průvodce vstupu uživatele se zavře a projekt je vytvořen z šablony.  
  
5.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na souboru se zdrojovým kódem a klikněte na tlačítko **zobrazit kód**.  
  
     Všimněte si, že `$custommessage$` byla nahrazena textem zadaným ve formuláři průvodce vstupu uživatele.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension – element (šablony sady Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
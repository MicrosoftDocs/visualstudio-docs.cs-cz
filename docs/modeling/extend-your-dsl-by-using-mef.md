---
title: Rozšíření vašeho DSL pomocí MEF
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8e4898ba6c87f25b38a6c3e42032412d69d8ece
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596603"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozšíření vašeho DSL pomocí MEF

Jazyk specifického pro doménu (DSL) můžete roztáhnout pomocí Managed Extensibility Framework (MEF). Vy nebo jiní vývojáři budete moct zapisovat rozšíření pro DSL beze změny definice DSL a kódu programu. Mezi taková rozšíření patří příkazy nabídky, obslužné rutiny přetažení a ověřování. Uživatelé budou moct nainstalovat DSL a pak pro něj nainstalovat rozšíření.

Kromě toho, když povolíte rozhraní MEF v DSL, může být snazší napsat některé funkce DSL, i když jsou vytvořeny společně s DSL.

Další informace o MEF naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Povolení rozšíření DSL na rozhraní MEF

1. V projektu **DslPackage** vytvořte novou složku s názvem **MefExtension** . Přidejte do něj následující soubory:

     Název souboru: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Nastavte identifikátor GUID v tomto souboru tak, aby byl stejný jako CommandSetId identifikátor GUID, který je definovaný v DslPackage\GeneratedCode\Constants.tt.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Název souboru: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Název souboru: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Název souboru: `ValidationExtensionRegistrar.tt`

    Pokud tento soubor přidáte, musíte v rámci DSL povolit ověřování pomocí aspoň jednoho přepínače v **EditorValidation** v Průzkumníku DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Název souboru: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. V projektu **DSL** vytvořte novou složku s názvem **MefExtension** . Přidejte do něj následující soubory:

     Název souboru: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Název souboru: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Název souboru: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Do existujícího souboru s názvem **DslPackage\Commands.vsct**přidejte následující řádek:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Vložte řádek po existující direktivě `<Include>`.

4. Otevřete *DslDefinition. DSL*.

5. V Průzkumníku DSL vyberte **Editor\Validation**.

6. V okno Vlastnosti zajistěte, aby alespoň jedna z vlastností s názvem **použití** byla `true`.

7. Na panelu nástrojů **Průzkumník řešení** klikněte na možnost **transformovat všechny šablony**.

     Soubory dceřiné společnosti se zobrazí pod každým přidaným soubory.

8. Sestavte a spusťte řešení a ověřte, zda stále pracuje.

Vaše DSL je teď povolená s podporou MEF. Můžete psát příkazy nabídky, obslužné rutiny gest a omezení ověřování jako rozšíření MEF. Tato rozšíření můžete v řešení DSL napsat společně s jiným vlastním kódem. Kromě toho můžete vy nebo jiní vývojáři napsat samostatná rozšíření sady Visual Studio, která šíří vaše DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Vytvoření rozšíření pro DSL podporující rozhraní MEF

Máte-li přístup k DSL podporujícímu MEF, kterou vytvořila nebo někomu jinému, můžete pro ni napsat rozšíření. Rozšíření lze použít k přidání příkazů nabídky, obslužných rutin gest nebo omezení ověřování. Chcete-li vytvořit tato rozšíření, použijte řešení rozšíření sady Visual Studio (VSIX). Řešení má dvě části: projekt knihovny tříd, který sestaví sestavení kódu a projekt VSIX, který zabalí sestavení.

### <a name="to-create-a-dsl-extension-vsix"></a>Vytvoření VSIX rozšíření DSL

1. Vytvořte nový projekt **knihovny tříd** .

2. V novém projektu přidejte odkaz na sestavení DSL.

   - Toto sestavení obvykle má název, který končí na. DSL. dll ".

   - Máte-li přístup k projektu DSL, můžete najít soubor sestavení v adresáři **DSL\\\\\***

   - Máte-li přístup k souboru VSIX DSL, můžete najít sestavení změnou přípony názvu souboru VSIX na ". zip". Dekomprimuje soubor. zip.

3. Přidejte odkazy na následující sestavení .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Vytvořte nový projekt **VSIX** projektu.

5. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt VSIX a vyberte **nastavit jako spouštěný projekt**.

6. V novém projektu otevřete **source. extension. vsixmanifest**.

7. Klikněte na **Přidat obsah**. V dialogovém okně nastavte **typ obsahu** na **součást MEF**a **zdrojový projekt** na projekt knihovny tříd.

8. Přidejte odkaz VSIX na DSL.

   1. Ve **zdroji. extension. vsixmanifest**klikněte na **Přidat odkaz** .

   2. V dialogovém okně klikněte na **Přidat datovou část** a pak vyhledejte soubor VSIX pro DSL. Soubor VSIX je sestaven v řešení DSL v **DslPackage\\bin\\\*** .

       To umožní uživatelům instalovat DSL a rozšíření ve stejnou dobu. Pokud uživatel už má nainstalovanou DSL, nainstaluje se jenom vaše rozšíření.

9. Zkontrolujte a aktualizujte ostatní pole **source. extension. vsixmanifest**. Klikněte na **Vybrat edice** a ověřte, jestli jsou nastavené správné edice sady Visual Studio.

10. Přidejte kód do projektu knihovny tříd. Jako vodítko použijte příklady v následující části.

     Můžete přidat libovolný počet tříd příkazu, gesto a ověřování.

11. Rozšíření otestujete stisknutím klávesy **F5**. V experimentální instanci sady Visual Studio vytvořte nebo otevřete ukázkový soubor DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Zápis rozšíření MEF pro DSL

Můžete zapisovat rozšíření v projektu kódu sestavení samostatného řešení s příponou DSL. Můžete také použít MEF v projektu DslPackage jako pohodlný způsob, jak psát příkazy, gesta a ověřovací kód jako součást DSL.

### <a name="menu-commands"></a>Příkazy nabídky

Pro zápis příkazu nabídky Definujte třídu, která implementuje <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> a prefixujte třídu s atributem definovaným v DSL s názvem *YourDsl*`CommandExtension`. Můžete napsat více než jednu třídu příkazu nabídky.

`QueryStatus()` se volá vždycky, když uživatel klikne pravým tlačítkem myši na diagram. Měl by zkontrolovat aktuální výběr a nastavit `command.Enabled`, které určují, kdy se má příkaz použít.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Obslužné rutiny gesta

Obslužná rutina gesta může pracovat s objekty přetaženými do diagramu odkudkoli, uvnitř nebo vně sady Visual Studio. Následující příklad umožní uživateli přetáhnout soubory z Průzkumníka Windows do diagramu. Vytvoří prvky, které obsahují názvy souborů.

Můžete napsat obslužné rutiny pro práci s přetažením z jiných modelů DSL a modelů UML. Další informace najdete v tématu [Postup: Přidání obslužné rutiny](../modeling/how-to-add-a-drag-and-drop-handler.md)přetažení myší.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Omezení ověřování

Metody ověřování jsou označeny atributem `ValidationExtension`, který je generován pomocí DSL, a také pomocí <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Metoda se může objevit v jakékoli třídě, která není označená atributem.

Další informace najdete v tématu [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Viz také:

- [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)

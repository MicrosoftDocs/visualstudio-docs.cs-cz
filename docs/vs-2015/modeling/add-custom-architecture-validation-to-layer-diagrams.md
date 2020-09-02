---
title: Přidání ověření vlastní architektury do diagramů vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b5ebe4e38878df209ab6065b1dbca88cd8404b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655308"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Přidání ověření vlastní architektury do diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio mohou uživatelé ověřit zdrojový kód v projektu proti modelu vrstvy, aby bylo možné ověřit, že zdrojový kód odpovídá závislostem v diagramu vrstev. Existuje standardní ověřovací algoritmus, ale můžete definovat vlastní ověřovací rozšíření.

 Když uživatel vybere příkaz **ověřit architekturu** v diagramu vrstvy, je vyvolána standardní metoda ověřování následovaný všemi nainstalovanými rozšířeními ověřování.

> [!NOTE]
> Ověřování v diagramu vrstev není stejné jako ověřování v diagramech UML. V diagramu vrstev je hlavním účelem porovnání diagramu s kódem programu v jiných částech řešení.

 Rozšíření pro ověření vrstvy můžete zabalit do rozšíření integrace sady Visual Studio (VSIX), které můžete distribuovat dalším uživatelům aplikace Visual Studio. Ověřovací modul můžete buď umístit do VSIX sami, nebo ho můžete zkombinovat na stejném VSIX jako další rozšíření. Kód validátoru byste měli napsat ve vlastním projektu sady Visual Studio, nikoli ve stejném projektu jako jiné rozšíření.

> [!WARNING]
> Po vytvoření projektu ověření zkopírujte [vzorový kód](#example) na konci tohoto tématu a pak ho upravte podle svých potřeb.

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definování validátoru vrstvy v novém VSIX
 Nejrychlejší způsob, jak vytvořit validátor, je použití šablony projektu. Tím se umístí kód a manifest VSIX do stejného projektu.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Definování rozšíření pomocí šablony projektu

1. Vytvořte projekt v novém řešení pomocí příkazu **Nový projekt** v nabídce **soubor** .

2. V dialogovém okně **Nový projekt** , v části **modelování projektů**, vyberte **rozšíření pro ověření návrháře vrstvy**.

    Šablona vytvoří projekt, který obsahuje malý příklad.

   > [!WARNING]
   > Aby šablona makethe fungovala správně:
   >
   > - Upravte volání na `LogValidationError` pro odebrání volitelných argumentů `errorSourceNodes` a `errorTargetNodes` .
   >   - Pokud používáte vlastní vlastnosti, použijte aktualizaci uvedenou v části [Přidání vlastních vlastností do diagramů vrstev](../modeling/add-custom-properties-to-layer-diagrams.md).

3. Upravte kód pro definování ověřování. Další informace najdete v tématu [ověřování programování](#programming).

4. Chcete-li otestovat rozšíření, viz [ladění při ověřování vrstvy](#debugging).

   > [!NOTE]
   > Vaše metoda bude volána pouze za určitých okolností a zarážky nebudou fungovat automaticky. Další informace naleznete v tématu [ladění ověřování vrstvy](#debugging).

5. Chcete-li nainstalovat rozšíření v hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo v jiném počítači, vyhledejte v *přihrádce \\ *soubor **. vsix** . Zkopírujte ho do počítače, kam ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, použijte **rozšíření a aktualizace** v nabídce **nástroje** .

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Přidání validátoru vrstvy do samostatného souboru VSIX
 Pokud chcete vytvořit jeden VSIX, který obsahuje validátory vrstvy, příkazy a další rozšíření, doporučujeme vytvořit jeden projekt pro definování VSIX a samostatné projekty pro obslužné rutiny. Informace o dalších typech rozšíření modelování najdete v tématu [rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Přidání ověření vrstvy do samostatného souboru VSIX

1. Vytvořte projekt knihovny tříd v novém nebo existujícím řešení sady Visual Studio. V dialogovém okně **Nový projekt** klikněte na položku **Visual C#** a potom klikněte na možnost **Knihovna tříd**. Tento projekt bude obsahovat třídu ověření vrstvy.

2. Identifikujte nebo vytvořte projekt VSIX ve vašem řešení. Projekt VSIX obsahuje soubor s názvem **source. extension. vsixmanifest**. Pokud je nutné přidat projekt VSIX, použijte následující postup:

    1. V dialogovém okně **Nový projekt** vyberte **Visual C#**, **rozšiřitelnost**, **projekt VSIX**.

    2. V **Průzkumník řešení**v místní nabídce projektu VSIX **nastavte jako projekt po spuštění**.

3. V části **source. extension. vsixmanifest**v části **assets (prostředky**) přidejte projekt ověření vrstvy jako komponentu MEF:

    1. Zvolte **Nové**.

    2. V dialogovém okně **Přidat nový prostředek** nastavte:

         **Typ**  =  **Microsoft. VisualStudio. MefComponent**

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Projekt**  =  *váš projekt validátoru*

4. Musíte ho také přidat jako ověření vrstvy:

    1. Zvolte **Nové**.

    2. V dialogovém okně **Přidat nový prostředek** nastavte:

         **Typ**  =  **Microsoft. VisualStudio. ArchitectureTools. Layer. validátor**. Nejedná se o jednu z možností v rozevíracím seznamu. Je nutné zadat ho z klávesnice.

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Projekt**  =  *váš projekt validátoru*

5. Vraťte se do projektu ověření vrstvy a přidejte následující odkazy projektu:

    |**Odkaz**|**Co vám to umožňuje**|
    |-------------------|------------------------------------|
    |Microsoft.VisualStudio.GraphModel.dll|Čtení grafu architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Čtení modelu DOM kódu přidruženého k vrstvám|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Čtení modelu vrstvy|
    |Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost|Čtení a aktualizace obrazců a diagramů.|
    |System. ComponentModel. složení|Definice ověřovací komponenty pomocí Managed Extensibility Framework (MEF)|
    |Microsoft. VisualStudio. Modeling. SDK. znění|Definování rozšíření modelování|

6. Zkopírujte ukázkový kód na konci tohoto tématu do souboru třídy v projektu knihovny validátoru, aby obsahoval kód pro ověření. Další informace najdete v tématu [ověřování programování](#programming).

7. Chcete-li otestovat rozšíření, viz [ladění při ověřování vrstvy](#debugging).

    > [!NOTE]
    > Vaše metoda bude volána pouze za určitých okolností a zarážky nebudou fungovat automaticky. Další informace naleznete v tématu [ladění ověřování vrstvy](#debugging).

8. Chcete-li nainstalovat VSIX v hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo v jiném počítači, vyhledejte soubor **. vsix** v adresáři **bin** projektu VSIX. Zkopírujte jej do počítače, kam chcete nainstalovat VSIX. Dvakrát klikněte na soubor VSIX v Průzkumníkovi Windows. (Průzkumník souborů v systému Windows 8.)

     Pokud ho chcete odinstalovat, použijte **rozšíření a aktualizace** v nabídce **nástroje** .

## <a name="programming-validation"></a><a name="programming"></a> Ověřování programování
 Chcete-li definovat rozšíření pro ověření vrstvy, Definujte třídu, která má následující vlastnosti:

- Celková forma deklarace je následující:

  ```

  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Když zjistíte chybu, můžete ji nahlásit pomocí `LogValidationError()` .

  > [!WARNING]
  > Nepoužívejte volitelné parametry `LogValidationError` .

  Když uživatel vyvolá příkaz nabídky **ověřit architekturu** , systém modulu runtime vrstvy analyzuje vrstvy a jejich artefakty a vytvoří tak graf. Graf obsahuje čtyři části:

- Modely vrstvy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které jsou reprezentovány jako uzly a odkazy v grafu.

- Kód, položky projektu a další artefakty, které jsou definovány v řešení a reprezentované jako uzly, a odkazy, které představují závislosti zjištěné procesem analýzy.

- Odkazy z uzlů vrstev na uzly artefaktů kódu.

- Uzly, které reprezentují chyby zjištěné validátorem.

  Když je graf vytvořen, je volána standardní metoda ověřování. Po dokončení se v nespecifikovaném pořadí zavolají jakékoli nainstalované metody ověřování rozšíření. Graf se předává každé `ValidateArchitecture` metodě, která může kontrolovat graf a nahlásit všechny nalezené chyby.

> [!NOTE]
> To není stejné jako proces ověření, který se používá pro diagramy UML, a není stejný jako proces ověření, který lze použít v jazycích specifických pro doménu.

 Metody ověřování by neměly měnit model vrstvy nebo kód, který se ověřuje.

 Model grafu je definován v <xref:Microsoft.VisualStudio.GraphModel> . Jeho hlavní třídy jsou <xref:Microsoft.VisualStudio.GraphModel.GraphNode> a <xref:Microsoft.VisualStudio.GraphModel.GraphLink> .

 Každý uzel a každý odkaz má jednu nebo více kategorií, které určují typ prvku nebo vztahu, který představuje. Uzly typického grafu mají následující kategorie:

- DSL. LayerModel

- DSL. Layer

- DSL. reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

  Odkazy z vrstev na elementy v kódu mají kategorii "představuje".

## <a name="debugging-validation"></a><a name="debugging"></a> Ověřování ladění
 Chcete-li ladit rozšíření ověřování vrstvy, stiskněte klávesy CTRL + F5. Otevře se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V této instanci otevřete nebo vytvořte model vrstvy. Tento model musí být přidružen k kódu a musí mít alespoň jednu závislost.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Testování pomocí řešení, které obsahuje závislosti
 Ověřování se neprovede, pokud nejsou k dispozici následující vlastnosti:

- V diagramu vrstev je alespoň jeden odkaz na závislost.

- V modelu jsou vrstvy, které jsou spojeny s prvky kódu.

  Při prvním spuštění experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro otestování rozšíření ověřování otevřete nebo vytvořte řešení, které má tyto vlastnosti.

### <a name="run-clean-solution-before-validate-architecture"></a>Před ověřením architektury spustit čisté řešení
 Vždy, když aktualizujete ověřovací kód, použijte příkaz **Vyčistit řešení** v nabídce **sestavení** v experimentálním řešení, než otestujete příkaz Validate. To je nezbytné, protože výsledky ověření jsou uloženy v mezipaměti. Pokud jste neaktualizovali diagram testovací vrstvy nebo jeho kód, metody ověřování nebudou provedeny.

### <a name="launch-the-debugger-explicitly"></a>Spustit ladicí program explicitně
 Ověřování se spouští v samostatném procesu. Proto se zarážky v metodě ověřování nebudou aktivovat. Ladicí program musíte připojit k procesu explicitně po spuštění ověřování.

 Chcete-li připojit ladicí program k procesu ověřování, vložte volání na `System.Diagnostics.Debugger.Launch()` začátek metody ověřování. Po zobrazení dialogového okna ladění vyberte hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Alternativně můžete vložit volání do `System.Windows.Forms.MessageBox.Show()` . Když se zobrazí okno se zprávou, přejděte na hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a v nabídce **ladění** klikněte na **připojit k procesu**. Vyberte proces s názvem **Graphcmd.exe**.

 Experimentální instanci vždy spusťte stisknutím kombinace kláves CTRL + F5 (**Spustit bez ladění**).

### <a name="deploying-a-validation-extension"></a>Nasazení rozšíření ověřování
 Chcete-li nainstalovat rozšíření ověřování na počítači, ve kterém je nainstalována vhodná verze sady Visual Studio, otevřete soubor VSIX v cílovém počítači. Chcete-li nainstalovat do počítače, na kterém [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] je nainstalována aplikace, je nutné ručně extrahovat obsah VSIX do složky rozšíření. Další informace najdete v tématu [nasazení rozšíření modelu vrstvy](../modeling/deploy-a-layer-model-extension.md).

## <a name="example-code"></a><a name="example"></a> Příklad kódu

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Viz také
 [Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)

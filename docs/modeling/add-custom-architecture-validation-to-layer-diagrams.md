---
title: Přidání vlastního ověřování architektury do diagramů závislostí
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e9343ed8fdb1f3993fcd5c2f70595fd4bdd92dcd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875447"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Přidání vlastního ověřování architektury do diagramů závislostí

V sadě Visual Studio uživatelé mohou ověřit zdrojový kód v projektu proti vrstvě modelu, tak, aby mohli ověřit, že zdrojový kód odpovídá závislostem na diagramu závislostí. Existuje standardní ověřovací algoritmus, ale můžete definovat vlastní rozšíření ověřování.

Když uživatel vybere **ověřit architekturu** příkaz na diagram závislostí, je vyvolána metoda standardního ověření, následovaný všemi rozšířeními ověření, které byly nainstalovány.

> [!NOTE]
> V diagramu závislostí je hlavním účelem ověření porovnat diagram pomocí programového kódu v dalších částech tohoto řešení.

Rozšíření ověření vrstvy můžete zabalit do Visual Studio integrace rozšíření (VSIX), které můžete distribuovat ostatním uživatelům aplikace Visual Studio. V rozšíření VSIX můžete umístit svůj validátor buď samostatně, nebo ho můžete zkombinovat ve stejném souboru VSIX jako další rozšíření. Měli byste psát kód validátoru ve svém vlastním projektu sady Visual Studio, není ve stejném projektu jako další rozšíření.

> [!WARNING]
> Po vytvoření projektu ověření zkopírujte [ukázkový kód](#example) na konci tohoto tématu a upravte, vlastních potřeb.

## <a name="requirements"></a>Požadavky

Zobrazit [požadavky](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definování ověřování vrstvy v novém souboru VSIX

Nejrychlejší způsob vytváření validátoru je použití šablony projektu. To umístí kód a VSIX manifest do stejného projektu.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Definování rozšíření pomocí šablony projektu

1. Vytvoření projektu v novém řešení pomocí **nový projekt** příkaz **souboru** nabídky.

2. V **nový projekt** dialogovém okně **projekty modelování**vyberte **rozšíření ověřování návrháře vrstev**.

    Šablona vytvoří projekt, který obsahuje malý příklad.

   > [!WARNING]
   > Chcete-li správnou funkčnost šablony:
   >
   > - Upravte volání `LogValidationError` odebrat volitelné argumenty `errorSourceNodes` a `errorTargetNodes`.
   > - Pokud používáte vlastní vlastnosti, použijte aktualizace uvedené v [přidání vlastních vlastností do diagramů závislostí](../modeling/add-custom-properties-to-layer-diagrams.md).

3. Upravte kód, aby definoval vaše ověření. Další informace najdete v tématu [programování ověření](#programming).

4. Chcete-li otestovat rozšíření, naleznete v tématu [ladění ověřování vrstev](#debugging).

   > [!NOTE]
   > Vaše metoda bude volána pouze za zvláštních okolností a zarážky nebudou fungovat automaticky. Další informace najdete v tématu [ladění ověřování vrstev](#debugging).

5. Chcete-li nainstalovat rozšíření v instanci hlavní aplikace Visual Studio nebo na jiném počítači, vyhledejte *VSIX* ve *bin* adresáře. Zkopírujte ho do počítače, ve které chcete nainstalovat a poklepejte na něj. Chcete-li ho odinstalovat, zvolte **rozšíření a aktualizace** na **nástroje** nabídky.

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Přidání validátoru vrstvy do samostatného souboru VSIX

Pokud chcete vytvořit jeden VSIX, který obsahuje validátory vrstvy, příkazy a další rozšíření, doporučujeme vytvořit jeden projekt k definování VSIX a samostatné projekty pro obslužné rutiny.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Přidání ověření vrstvy do samostatného souboru VSIX

1.  Vytvořte projekt knihovny tříd v nové nebo existující řešení sady Visual Studio. V **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** a potom klikněte na tlačítko **knihovny tříd**. Tento projekt bude obsahovat třídu ověřování vrstvy.

2.  Určete nebo vytvořte VSIX projekt ve vašem řešení. Projekt VSIX obsahuje soubor s názvem **source.extension.vsixmanifest**. Pokud budete muset přidat projekt VSIX, postupujte podle těchto kroků:

    1.  V **nový projekt** dialogového okna zvolte **Visual C#**, **rozšiřitelnost**, **projekt VSIX**.

    2.  V **Průzkumníka řešení**, v místní nabídce projektu VSIX **nastavit jako spouštěný projekt**.

3.  V **source.extension.vsixmanifest**v části **prostředky**, přidejte vrstvu ověřování projektu jako komponentu MEF:

    1.  Zvolte **nové**.

    2.  V **přidat nové aktivum** dialogovém okně nastavení:

         **Type** = **Microsoft.VisualStudio.MefComponent**

         **Zdroj** = **projekt v aktuálním řešení**

         **Projekt** = *projektu program pro ověření*

4.  Musíte taky přidat ji jako vrstvu ověřování:

    1.  Zvolte **nové**.

    2.  V **přidat nové aktivum** dialogovém okně nastavení:

         **Type** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. To však není jednou z možností v rozevíracím seznamu. Je nutné zadat z klávesnice.

         **Zdroj** = **projekt v aktuálním řešení**

         **Projekt** = *projektu program pro ověření*

5.  Vraťte se do projektu ověření vrstvy a přidejte následující odkazy projektu:

    |**Referenční informace**|**To umožňuje provést**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Přečtěte si graf architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Přečtěte si, že v modelu DOM kódu spojený s vrstvami|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Přečtěte si model vrstva|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Číst a aktualizovat tvary a diagramy.|
    |System.ComponentModel.Composition|Definovat součást ověřování pomocí Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Definovat rozšíření modelování|

6.  Zkopírujte ukázkový kód na konci tohoto tématu do souboru třídy v projektu knihovny ověřování tak, aby obsahovala kód pro ověření. Další informace najdete v tématu [programování ověření](#programming).

7.  Chcete-li otestovat rozšíření, naleznete v tématu [ladění ověřování vrstev](#debugging).

    > [!NOTE]
    > Vaše metoda bude volána pouze za zvláštních okolností a zarážky nebudou fungovat automaticky. Další informace najdete v tématu [ladění ověřování vrstev](#debugging).

8.  Chcete-li nainstalovat VSIX v instanci hlavní aplikace Visual Studio nebo na jiném počítači, vyhledejte **VSIX** soubor **bin** adresáře projektu VSIX. Zkopírujte ho do počítače, ve které chcete nainstalovat VSIX. Poklikejte na soubor VSIX v Průzkumníku Windows.

     Chcete-li ho odinstalovat, použijte **rozšíření a aktualizace** na **nástroje** nabídky.

##  <a name="programming"></a> Ověření programování

K definování ověření přípony vrstvy definujete třídu, která má následující vlastnosti:

- Celková forma deklarace je následující:

  ```csharp
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

- Pokud zjistíte chybu, můžete ji ohlásit pomocí `LogValidationError()`.

  > [!WARNING]
  > Nepoužívejte volitelné parametry `LogValidationError`.

Pokud uživatel vyvolá **ověřit architekturu** příkaz nabídky, systém modulu runtime vrstvy zanalyzuje vrstvy a jejich artefakty k vytvoření grafu. Graf má čtyři části:

- Modely vrstvy řešení aplikace Visual Studio, které jsou reprezentovány jako uzly a odkazy v grafu.

- Kód, položky projektu a další artefakty, které jsou definovány v řešení a reprezentovány jako uzly a odkazy, které představují závislosti zjištěné v procesu analýzy.

- Propojení z uzlů vrstvy do uzlů kódových artefaktů.

- Uzly, které představují chyby zjištěné validátorem.

Pokud byl vytvořen graf, je volána metoda standardního ověření. Po jejím dokončení, všechny metody nainstalovaných rozšíření ověřování jsou zavolány v nespecifikovaném pořadí. Graf je předán pro každou `ValidateArchitecture` metodu, která může prohledávat graf a podávat zprávy o chybách, které nalezne.

> [!NOTE]
> To však není stejný jako proces ověření, který lze použít v jazycích specifické pro doménu.

Metody ověřování by neměly měnit model vrstvy nebo kód, který se ověřuje.

Model grafu je definován v <xref:Microsoft.VisualStudio.GraphModel>. Jeho hlavní třídy jsou <xref:Microsoft.VisualStudio.GraphModel.GraphNode> a <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Každý uzel a každý odkaz má jednu nebo více kategorií, které určují typ prvku nebo vztahu, který představuje. Uzly typického grafu jsou následující kategorie:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Propojení z vrstev do prvků v kódu mají kategorii "Představuje".

##  <a name="debugging"></a> Ladění ověřování

Chcete-li ladit rozšíření ověřování vrstvy, stiskněte CTRL + F5. Otevře se experimentální instanci sady Visual Studio. V tomto případě otevřete nebo vytvořte model vrstev. Tento model musí být přidružen ke kódu a musí mít alespoň jednu závislost.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Otestujte řešení, která obsahuje závislosti

Ověření není provedena, pokud jsou k dispozici následující vlastnosti:

- Na diagram závislostí je alespoň jeden odkaz závislosti.

- Existují vrstvy v modelu, které jsou spojeny s prvky kódu.

Při prvním spuštění experimentální instanci sady Visual Studio k testování rozšíření ověřování otevřete nebo vytvořte řešení, které má tyto vlastnosti.

### <a name="run-clean-solution-before-validate-architecture"></a>Spusťte čisté řešení před ověřením architektury

Pokaždé, když aktualizujete kód pro ověření, použijte **Vyčistit řešení** příkaz **sestavení** nabídky v experimentálním řešení před otestováním příkazu ověřit. To je nezbytné, protože výsledky ověření jsou ukládány do mezipaměti. Pokud jste neaktualizovali diagram testovací závislostí nebo jeho kód, nebude provedeno metody ověřování.

### <a name="launch-the-debugger-explicitly"></a>Spustit ladicí program explicitně

Ověřování je spuštěno v samostatném procesu. Zarážky ve vaší metodě ověřování tedy nebudou aktivovány. Je nutné připojit ladicí program k procesu explicitně po spuštění ověření.

Chcete-li připojit ladicí program k procesu ověřování, vložte volání `System.Diagnostics.Debugger.Launch()` na začátku své metody ověřování. Jakmile se zobrazí dialogové okno ladění, vyberte hlavní instanci aplikace Visual Studio.

Alternativně můžete vložit volání do `System.Windows.Forms.MessageBox.Show()`. Když se objeví okno zpráv, přejděte na hlavní instanci aplikace Visual Studio a na **ladění** klikněte na nabídku **připojit k procesu**. Vyberte proces, který je pojmenován **Graphcmd.exe**.

Experimentální instanci vždy spusťte stisknutím kombinace kláves CTRL + F5 (**spustit bez ladění**).

### <a name="deploying-a-validation-extension"></a>Nasazení rozšíření ověřování

Chcete-li nainstalovat rozšíření ověřování v počítači, na kterém je nainstalován vhodnou verzi sady Visual Studio, otevřete soubor VSIX v cílovém počítači.

##  <a name="example"></a> Příklad kódu

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

- [Rozšíření diagramů závislostí](../modeling/extend-layer-diagrams.md)

---
title: Přidání vlastního ověřování architektury do diagramů závislostí
description: Tento článek obsahuje informace o tom, jak přidat vlastní ověření architektury do diagramů závislostí.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: cc00f86bafebd14177400ffa0ee596a733e9fb28
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384626"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Přidání vlastního ověřování architektury do diagramů závislostí

V Visual Studio mohou uživatelé ověřit zdrojový kód v projektu proti modelu vrstev, aby mohli ověřit, že zdrojový kód odpovídá závislostem v diagramu závislostí. K dispozici je standardní ověřovací algoritmus, ale můžete definovat vlastní rozšíření ověřování.

Když uživatel vybere  příkaz Ověřit architekturu v diagramu závislostí, vyvolá se standardní metoda ověřování následovaná libovolnými nainstalovanými rozšířeními ověřování.

> [!NOTE]
> V diagramu závislostí je hlavním účelem ověřování porovnat diagram s kódem programu v jiných částech řešení.

Rozšíření pro ověřování vrstev můžete zabalit do rozšíření Visual Studio Integration Extension (VSIX), které můžete distribuovat dalším Visual Studio uživatelům. Validátor můžete buď umístit do VSIX sám, nebo ho můžete zkombinovat do stejného VSIX jako ostatní rozšíření. Kód validátoru byste měli napsat ve vlastním projektu Visual Studio, nikoli ve stejném projektu jako ostatní rozšíření.

> [!WARNING]
> Po vytvoření projektu ověřování zkopírujte [](#example) příklad kódu na konci tohoto tématu a pak ho upravte podle svých potřeb.

## <a name="requirements"></a>Požadavky

Viz [Požadavky.](../modeling/extend-layer-diagrams.md#requirements)

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definování validátoru vrstev v novém souboru VSIX

Nejrychlejší metodou vytvoření validátoru je použití šablony projektu. Tím se kód a manifest VSIX umístí do stejného projektu.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Definování rozšíření pomocí šablony projektu

1. Vytvořte nový projekt **rozšíření ověřování návrháře** vrstev.

    Šablona vytvoří projekt, který obsahuje malý příklad.

   > [!WARNING]
   > Správné fungování šablony:
   >
   > - Upravte volání `LogValidationError` metody pro odebrání volitelných argumentů a `errorSourceNodes` `errorTargetNodes` .
   > - Pokud používáte vlastní vlastnosti, použijte aktualizaci uvedenou v části [Přidání vlastních vlastností do diagramů závislostí](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Upravte kód a definujte ověřování. Další informace najdete v tématu [Programovací ověřování](#programming).

3. Pokud chcete rozšíření otestovat, podívejte se na [ladění ověření vrstvy](#debugging).

   > [!NOTE]
   > Vaše metoda bude volána pouze za určitých okolností a zarážky nebudou fungovat automaticky. Další informace najdete v tématu [Ladění ověření vrstvy.](#debugging)

::: moniker range="vs-2017"

4. Pokud chcete rozšíření nainstalovat do hlavní instance Visual Studio nebo na jiný počítač, vyhledejte *soubor .vsix* v *adresáři bin.* Zkopírujte ho do počítače, do kterého ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, **zvolte Rozšíření a aktualizace** v **nabídce** Nástroje.

::: moniker-end

::: moniker range=">=vs-2019"

4. Pokud chcete rozšíření nainstalovat do hlavní instance Visual Studio nebo na jiný počítač, vyhledejte *soubor .vsix* v *adresáři bin.* Zkopírujte ho do počítače, do kterého ho chcete nainstalovat, a dvakrát na něj klikněte. Pokud ho chcete odinstalovat, **zvolte Spravovat** rozšíření **v nabídce** Rozšíření.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Přidání validátoru vrstev do samostatného souboru VSIX

Pokud chcete vytvořit jeden VSIX, který obsahuje validátory vrstev, příkazy a další rozšíření, doporučujeme vytvořit jeden projekt, který definuje VSIX, a samostatné projekty pro obslužné rutiny.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Přidání ověřování vrstev do samostatného VSIX

1. Vytvořte nový **projekt knihovny** tříd. Tento projekt bude obsahovat třídu ověřování vrstev.

2. Vyhledejte nebo vytvořte **ve svém řešení projekt VSIX.** Projekt VSIX obsahuje soubor s názvem **source.extension.vsixmanifest**.

3. V **Průzkumník řešení** klikněte pravým tlačítkem na nabídku projektu VSIX a zvolte **Nastavit jako spouštěný projekt.**

4. V **souboru source.extension.vsixmanifest** v části **Prostředky** přidejte projekt ověřování vrstev jako komponentu MEF:

    1. Zvolte **Nové**.

    2. V dialogovém **okně Přidat nový** prostředek nastavte:

         **Typ**  =  **Microsoft.VisualStudio.MefComponent**

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Project (Projekt)**  =  *váš projekt validátoru*

5. Musíte ho také přidat jako ověření vrstvy:

    1. Zvolte **Nové**.

    2. V dialogovém **okně Přidat nový** prostředek nastavte:

         **Typ**  =  **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Toto není jedna z možností v rozevíracím seznamu. Musíte ho zadat z klávesnice.

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Project (Projekt)**  =  *váš projekt validátoru*

6. Vraťte se do projektu ověřování vrstev a přidejte následující odkazy na projekt:

    |**Odkaz**|**Co vám to umožňuje dělat**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Čtení grafu architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Čtení kódu modelu DOM přidruženého k vrstvám|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Čtení modelu vrstev|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Čtení a aktualizace obrazců a diagramů|
    |System.ComponentModel.Composition|Definování ověřovací komponenty pomocí Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk. [version]|Definování rozšíření modelování|

7. Zkopírujte kód příkladu na konci tohoto tématu do souboru třídy v projektu knihovny validátoru, který bude obsahovat kód pro vaše ověření. Další informace najdete v tématu [Programovací ověřování](#programming).

8. Pokud chcete rozšíření otestovat, podívejte se na [ladění ověření vrstvy](#debugging).

    > [!NOTE]
    > Vaše metoda bude volána pouze za určitých okolností a zarážky nebudou fungovat automaticky. Další informace najdete v tématu [Ladění ověření vrstvy.](#debugging)

9. Pokud chcete nainstalovat VSIX v hlavní instanci Visual Studio nebo na jiném počítači, vyhledejte **soubor .vsix** v adresáři **bin** projektu VSIX. Zkopírujte ho do počítače, do kterého chcete nainstalovat VSIX. Poklikejte na soubor VSIX v Průzkumník Windows.

## <a name="programming-validation"></a><a name="programming"></a> Programovací ověřování

Chcete-li definovat rozšíření ověřování vrstev, definujete třídu, která má následující vlastnosti:

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

- Když zjistíte chybu, můžete ji nahlásit pomocí `LogValidationError()` příkazu .

  > [!WARNING]
  > Nepovinné parametry pro `LogValidationError` nepoužívejte.

Když uživatel vyvolá příkaz nabídky **Ověřit** architekturu, systém modulu runtime vrstvy analyzuje vrstvy a jejich artefakty a vytvoří graf. Graf má čtyři části:

- Modely vrstev v Visual Studio, které jsou reprezentované jako uzly a propojení v grafu.

- Kód, položky projektu a další artefakty, které jsou definovány v řešení a reprezentovány jako uzly, a odkazy, které představují závislosti zjištěné procesem analýzy.

- Odkazuje z uzlů vrstvy na uzly artefaktů kódu.

- Uzly, které představují chyby zjištěné validátorem.

Po zkonstruování grafu se volá standardní ověřovací metoda. Po dokončení jsou všechny nainstalované metody ověřování rozšíření volány v neurčeném pořadí. Graf se předává každé metodě, která může prohledat graf a nahlásit `ValidateArchitecture` případné chyby, které najde.

> [!NOTE]
> To není totéž jako proces ověřování, který lze použít v jazycích specifických pro doménu.

Metody ověřování by neměly měnit model vrstev ani kód, který se ověřuje.

Grafový model je definovaný v <xref:Microsoft.VisualStudio.GraphModel> . Jeho hlavní třídy jsou a <xref:Microsoft.VisualStudio.GraphModel.GraphNode> <xref:Microsoft.VisualStudio.GraphModel.GraphLink> .

Každý uzel a každý odkaz mají jednu nebo více kategorií, které určují typ prvku nebo relace, které představuje. Uzly typického grafu mají následující kategorie:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Odkazy z vrstev na prvky v kódu mají kategorii "Představuje".

## <a name="debugging-validation"></a><a name="debugging"></a> Ověřování ladění

Pokud chcete ladit rozšíření ověřování vrstev, stiskněte kombinaci kláves CTRL+F5. Otevře se experimentální Visual Studio aplikace. V tomto případě otevřete nebo vytvořte model vrstev. Tento model musí být přidružený ke kódu a musí mít alespoň jednu závislost.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Testování s řešením, které obsahuje závislosti

Ověření se provede pouze v případě, že jsou přítomny následující vlastnosti:

- V diagramu závislostí je alespoň jedno propojení závislostí.

- V modelu existují vrstvy, které jsou přidruženy k prvkům kódu.

Při prvním spuštění experimentální instance Visual Studio rozšíření pro ověřování otevřete nebo vytvořte řešení, které má tyto vlastnosti.

### <a name="run-clean-solution-before-validate-architecture"></a>Spuštění čistého řešení před ověřením architektury

Pokaždé, když aktualizujete  ověřovací kód,  použijte před otestování příkazu Ověřit příkaz Vyčistit řešení v nabídce Sestavení v experimentálním řešení. To je nezbytné, protože výsledky ověření jsou uložené v mezipaměti. Pokud jste ne aktualizované testovací diagram závislostí nebo jeho kód, metody ověřování nebudou provedeny.

### <a name="launch-the-debugger-explicitly"></a>Explicitní spuštění ladicího programu

Ověřování se spouští v samostatném procesu. Proto se zarážky ve vaší metodě ověřování nespouštějí. Ladicí program je nutné k procesu připojit explicitně po zahájení ověřování.

Chcete-li připojit ladicí program k procesu ověřování, vložte na začátek ověřovací `System.Diagnostics.Debugger.Launch()` metody volání metody . Po zobrazení dialogového okna ladění vyberte hlavní instanci Visual Studio.

Případně můžete vložit volání `System.Windows.Forms.MessageBox.Show()` . Jakmile se zobrazí okno se zprávou, přejděte na hlavní instanci Visual Studio a v nabídce **Ladit** klikněte **na Připojit k procesu**. Vyberte proces s názvem **Graphcmd.exe**.

Experimentální instanci vždy spustíte stisknutím kombinace kláves CTRL+F5 (**Spustit bez ladění**).

### <a name="deploying-a-validation-extension"></a>Nasazení rozšíření pro ověřování

Pokud chcete rozšíření pro ověření nainstalovat na počítač, na kterém je nainstalovaná vhodná Visual Studio, otevřete v cílovém počítači soubor VSIX.

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

- [Rozšíření diagramů závislostí](../modeling/extend-layer-diagrams.md)

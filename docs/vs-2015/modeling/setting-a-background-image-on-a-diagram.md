---
title: Nastavení obrázku pozadí v diagramu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671208"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Nastavení obrázku pozadí v diagramu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vizualizace a modelování sady SDK můžete nastavit obrázek pozadí pro vygenerovaný Návrhář pomocí vlastního kódu.

## <a name="setting-the-background-image"></a>Nastavení obrázku pozadí

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Nastavení obrázku pozadí pro vygenerovaný Návrhář

1. Zkopírujte soubor obrázku, který chcete použít jako pozadí diagramu, do adresáře Dsl\Resources pro aktuální projekt.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku Dsl\Resources, přejděte na **Přidat**a pak klikněte na **existující položka**.

3. V dialogovém okně **Přidat existující položku** přejděte do složky Dsl\Resources.

4. V seznamu **soubory typu** klikněte na **soubory obrázků**.

5. Klikněte na soubor obrázku, který jste zkopírovali do adresáře, a pak klikněte na **Přidat**.

6. Klikněte pravým tlačítkem na DSL a kliknutím na **vlastnosti** otevřete vlastnosti projektu DSL.

7. Na kartě **prostředky** klikněte na **Tento projekt neobsahuje soubor výchozích prostředků. Pokud ho chcete vytvořit, klikněte sem.**

8. Přidejte soubor obrázku do souboru prostředků přetažením obrázku z **Průzkumník řešení** do okna Resources (prostředky).

9. Otevřete nabídku soubor a kliknutím na možnost uložte vlastnosti projektu.

10. Ověřte, že soubor Dsl\Properties\Resources.resx existuje a má pod ním soubor Resources.Designer.cs.

11. Pokud chybí Resources.Designer.cs, klikněte na soubor Resources. resx v **Průzkumník řešení**.

12. V okně **vlastnosti** nastavte vlastnost `Custom Tool` na hodnotu `ResXFileCodeGenerator`.

13. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt DSL, přejděte na **Přidat**a klikněte na **Nová složka**.

14. Pojmenujte složku **Custom**.

15. Klikněte pravým tlačítkem myši na vlastní složku, přejděte na **Přidat**a klikněte na **Nová položka**.

16. V dialogovém okně **Přidat novou položku** v seznamu **šablony** klikněte na **soubor kódu**.

17. Do pole **název** zadejte `BackgroundImage.cs` a klikněte na **Přidat**.

18. Zkopírujte následující kód do souboru BackgroundImage.cs, upravte obor názvů, název třídy diagramu a název prostředku obrázkového souboru.

     Nahraďte "MyDiagramClass" názvem částečné třídy diagramu, která je definována v Dsl\GeneratedCode\Diagrams.cs. Správný obor názvů můžete také načíst ze souboru Dsl\GeneratedCode\Diagrams.cs.

    ```
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Další informace o přizpůsobení modelu pomocí programového kódu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také
 [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md) [přizpůsobení textových a obrazových polí](../modeling/customizing-text-and-image-fields.md) [procházení a aktualizace modelu v psaní kódu programového kódu](../modeling/navigating-and-updating-a-model-in-program-code.md) [pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)

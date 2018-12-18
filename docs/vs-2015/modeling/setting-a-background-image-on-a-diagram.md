---
title: Nastavení obrázku pozadí v diagramu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd9d5ca21dbe1b0444c650a127fc0184dfb640f1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240549"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Nastavení obrázku pozadí v diagramu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, můžete nastavit obrázek pozadí pro vygenerovaného návrháře pomocí vlastního kódu.  
  
## <a name="setting-the-background-image"></a>Nastavení obrázku pozadí  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Nastavit obrázek pozadí pro vygenerovaného návrháře  
  
1.  Zkopírujte soubor obrázku, který chcete použít jako pozadí diagramu do adresáře Dsl\Resources pro aktuální projekt.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku Dsl\Resources, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**.  
  
3.  V **přidat existující položku** dialogové okno, přejděte do složky Dsl\Resources.  
  
4.  V **soubory typu** klikněte na možnost **soubory bitových kopií**.  
  
5.  Klikněte na soubor obrázku, který jste zkopírovali do adresáře a potom klikněte na tlačítko **přidat**.  
  
6.  Klikněte pravým tlačítkem na Dsl a klikněte na tlačítko **vlastnosti** otevřete vlastnosti projektu Dsl.  
  
7.  Na **prostředky** klikněte na tlačítko **tento projekt neobsahuje soubor výchozích prostředků. Vytvořte si ho kliknutím sem.**  
  
8.  Přidat soubor bitové kopie do souboru prostředků přetažením obrázek ze **Průzkumníka řešení** do okna zdroje.  
  
9. Otevřete nabídku Soubor a klikněte na možnost Uložit vlastnosti projektu.  
  
10. Ověřte, že soubor Dsl\Properties\Resources.resx existuje a má soubor Resources.Designer.cs pod ním.  
  
11. Pokud chybí Resources.Designer.cs, klikněte na soubor Resources.resx v **Průzkumníka řešení**.  
  
12. V **vlastnosti** okno, nastaveno `Custom Tool` vlastnost `ResXFileCodeGenerator`.  
  
13. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt Dsl, přejděte na **přidat**a klikněte na tlačítko **novou složku**.  
  
14. Název složky **vlastní**.  
  
15. Klikněte pravým tlačítkem na vlastní složku, přejděte na **přidat**a klikněte na tlačítko **nová položka**.  
  
16. V **přidat novou položku** v dialogu **šablony** klikněte na možnost **souboru s kódem**.  
  
17. V **název** zadejte `BackgroundImage.cs`a klikněte na tlačítko **přidat**.  
  
18. Zkopírujte následující kód do souboru BackgroundImage.cs nastavení oboru názvů, název diagramu třídy a název souboru prostředku bitové kopie.  
  
     Nahraďte názvem částečné třídy diagram, který je definován v Dsl\GeneratedCode\Diagrams.cs "MyDiagramClass". Můžete také načíst správný obor názvů ze souboru Dsl\GeneratedCode\Diagrams.cs.  
  
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
  
     Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md)   
 [Přizpůsobení textových a obrazových polí](../modeling/customizing-text-and-image-fields.md)   
 [Procházení a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)




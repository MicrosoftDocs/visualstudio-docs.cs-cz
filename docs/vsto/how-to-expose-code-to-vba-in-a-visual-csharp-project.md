---
title: 'Postupy: vystavení kódu pro jazyk VBA v projektu jazyka C#'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544830"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Postupy: vystavení kódu pro jazyk VBA v projektu jazyka Visual C#
  Můžete vystavit kód v projektu jazyka Visual C# do kódu jazyk Visual Basic for Application (VBA), pokud chcete, aby oba typy kódu byly vzájemně spolupracovaly.

 Proces jazyka Visual C# se liší od Visual Basicho procesu. Další informace naleznete v tématu [How to: vystavení kódu pro jazyk VBA v projektu Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Vystavení kódu v projektu jazyka Visual C#
 Chcete-li povolit kód v jazyce VBA pro volání kódu v projektu jazyka Visual C#, upravte kód tak, aby byl viditelný pro model COM, a poté v Návrháři nastavte vlastnost **ReferenceAssemblyFromVbaProject** na **hodnotu true** .

 Návod, který ukazuje, jak zavolat metodu v projektu jazyka Visual C# z jazyka VBA, naleznete v tématu [Návod: volání kódu z jazyka VBA v projektu jazyka Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Vystavení kódu v projektu jazyka Visual C# pro jazyk VBA

1. Otevřete nebo vytvořte projekt na úrovni dokumentu, který je založen na dokumentu aplikace Word, excelovém sešitu nebo šabloně aplikace Excel, který podporuje makra a který již obsahuje kód VBA.

    Další informace o formátech souborů dokumentů, které podporují makra, najdete v tématu [kombinování úprav na úrovni dokumentu VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Tuto funkci nelze použít v projektech šablon aplikace Word.

2. Ujistěte se, že kód VBA v dokumentu může běžet bez výzvy uživateli, aby povolil makra. Můžete důvěřovat kódu VBA pro spuštění přidáním umístění projektu Office do seznamu důvěryhodných umístění v nastavení centra zabezpečení pro Word nebo Excel.

3. Přidejte člena, který chcete zpřístupnit pro jazyk VBA, do veřejné třídy v projektu a deklarujte nového člena jako **veřejné**.

4. Použijte následující <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy a <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> pro třídu, kterou vystavujete do jazyka VBA. Tyto atributy nastaví třídu jako viditelnou pro model COM, ale bez generování rozhraní třídy.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Přepište metodu **GetAutomationObject** třídy hostitelské položky v projektu tak, aby vracela instanci třídy, kterou vystavujete do jazyka VBA:

   - Pokud zveřejňujete třídu hostitelské položky do jazyka VBA, přepište metodu **GetAutomationObject** , která patří do této třídy, a vraťte aktuální instanci třídy.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Pokud vystavuje třídu, která není položkou hostitele v jazyce VBA, přepište metodu **GetAutomationObject** jakékoli položky hostitele v projektu a vraťte instanci třídy položky mimo hostitele. Například následující kód předpokládá, že zveřejňujete třídu s názvem `DocumentUtilities` do jazyka VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Další informace o položkách hostitelů naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

6. Extrahujte rozhraní ze třídy, kterou vystavujete do jazyka VBA. V dialogovém okně **rozbalte rozhraní** vyberte veřejné členy, které chcete zahrnout do deklarace rozhraní. Další informace najdete v tématu [extrakce refaktoringu rozhraní](../ide/reference/extract-interface.md).

7. Přidejte klíčové slovo **Public** do deklarace rozhraní.

8. Nastavte rozhraní jako viditelné pro model COM přidáním následujícího <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributu do rozhraní.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Otevřete dokument (pro Word) nebo list (pro Excel) v návrháři v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. V okně **vlastnosti** vyberte vlastnost **ReferenceAssemblyFromVbaProject** a změňte hodnotu na **true**.

    > [!NOTE]
    > Pokud sešit nebo dokument ještě neobsahuje kód VBA nebo pokud kód VBA v dokumentu není důvěryhodný ke spuštění, zobrazí se při nastavování vlastnosti **ReferenceAssemblyFromVbaProject** na **hodnotu true**chybová zpráva. Je to proto, že Visual Studio nemůže v této situaci upravovat projekt VBA v dokumentu.

11. Ve zprávě, která se zobrazí, klikněte na **OK** . Tato zpráva vás provede tím, že pokud přidáte kód VBA do sešitu nebo dokumentu při spuštění projektu z nástroje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kód VBA bude při příštím sestavení projektu ztracen. Důvodem je, že dokument ve výstupní složce sestavení je přepsán při každém sestavení projektu.

     V tomto okamžiku Visual Studio nakonfiguruje projekt tak, aby projekt VBA mohl zavolat do sestavení. Visual Studio také přidá metodu s názvem `GetManagedClass` do projektu VBA. Tuto metodu můžete zavolat z libovolného místa v projektu VBA pro přístup ke třídě, kterou jste vystavili v jazyce VBA.

12. Sestavte projekt.

## <a name="see-also"></a>Viz také:
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Návod: volání kódu z jazyka VBA ve Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)

---
title: 'Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA'
description: Přečtěte si, jak můžete vystavit kód v Visual Basic projektu do kódu jazyk Visual Basic for Application (VBA), pokud chcete, aby mezi nimi vzájemně spolupracovaly dva typy kódu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61f94ebb5ed0c5e76693ddc8c0717b6adf9222f3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845983"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA
  Kód v projektu můžete vystavit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] jazyk Visual Basic for Application (VBA), pokud chcete, aby mezi nimi byly vzájemně spolupracovaly dva typy kódu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Proces Visual Basic se liší od procesu Visual C#. Další informace naleznete v tématu [How to: vystavení kódu pro jazyk VBA ve Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Tento proces se liší od kódu v třídě položky hostitele, než je pro kód v jiných třídách:

- [Vystavení kódu v třídě položky hostitele](#HostItemCode)

- [Vystavení kódu, který není v třídě hostitelské položky](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Vystavení kódu v třídě položky hostitele
 Chcete-li povolit kód v jazyce VBA pro volání kódu Visual Basic v třídě položky hostitele, nastavte vlastnost **EnableVbaCallers** položky hostitele na **hodnotu true**.

 Návod, který ukazuje, jak vystavit metodu třídy položky hostitele a pak ji volat z jazyka VBA, naleznete v tématu [Návod: volání kódu z jazyka VBA v projektu Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Další informace o položkách hostitelů naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Vystavení kódu v položce hostitele v jazyce VBA

1. Otevřete nebo vytvořte projekt na úrovni dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , který je založen na dokumentu aplikace Word, excelovém sešitu nebo šabloně aplikace Excel, který podporuje makra a který již obsahuje kód VBA.

     Další informace o formátech souborů dokumentů, které podporují makra, najdete v tématu [kombinování úprav na úrovni dokumentu VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Tuto funkci nelze použít v projektech šablon aplikace Word.

2. Ujistěte se, že kód VBA v dokumentu může běžet bez výzvy uživateli, aby povolil makra. Můžete důvěřovat kódu VBA pro spuštění přidáním umístění projektu Office do seznamu důvěryhodných umístění v nastavení centra zabezpečení pro Word nebo Excel.

3. Přidejte vlastnost, metodu nebo událost, které chcete zpřístupnit pro jazyk VBA, pro jednu z tříd hostitelských položek v projektu a deklarujte nového člena jako **veřejné**. Název třídy závisí na aplikaci:

    - Ve wordovém projektu je třída položky hostitele pojmenována `ThisDocument` ve výchozím nastavení.

    - V projektu aplikace Excel jsou třídy hostitelských položek pojmenovány `ThisWorkbook` , `Sheet1` , `Sheet2` a `Sheet3` ve výchozím nastavení.

4. U položky hostitel nastavte vlastnost **EnableVbaCallers** na **hodnotu true**. Tato vlastnost je k dispozici v okně **vlastnosti** , když je položka hostitele v Návrháři otevřená.

     Po nastavení této vlastnosti sada Visual Studio automaticky nastaví vlastnost **ReferenceAssemblyFromVbaProject** na **hodnotu true**.

    > [!NOTE]
    > Pokud sešit nebo dokument ještě neobsahuje kód VBA nebo pokud kód VBA v dokumentu není důvěryhodný ke spuštění, zobrazí se při nastavování vlastnosti **EnableVbaCallers** na **hodnotu true** chybová zpráva. Je to proto, že Visual Studio nemůže v této situaci upravovat projekt VBA v dokumentu.

5. Ve zprávě, která se zobrazí, klikněte na **OK** . Tato zpráva vás provede tím, že pokud přidáte kód VBA do sešitu nebo dokumentu, ze kterého spouštíte projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kód VBA bude při příštím sestavení projektu ztracen. Důvodem je, že dokument ve výstupní složce sestavení je přepsán při každém sestavení projektu.

     V tomto okamžiku Visual Studio nakonfiguruje projekt tak, aby projekt VBA mohl zavolat do sestavení. Visual Studio také přidá vlastnost s názvem `CallVSTOAssembly` do `ThisDocument` modulu, `ThisWorkbook` , `Sheet1` , `Sheet2` nebo `Sheet3` v projektu VBA. Tuto vlastnost můžete použít pro přístup k veřejným členům třídy, které jsou zpřístupněny v jazyce VBA.

6. Sestavte projekt.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Vystavení kódu, který není v třídě hostitelské položky
 Chcete-li povolit kód v jazyce VBA pro volání kódu Visual Basic, který není v třídě položky hostitele, upravte kód tak, aby byl viditelný pro jazyk VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Vystavení kódu, který není v třídě položky hostitele v jazyce VBA

1. Otevřete nebo vytvořte projekt na úrovni dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , který je založen na dokumentu aplikace Word, excelovém sešitu nebo šabloně aplikace Excel, který podporuje makra a který již obsahuje kód VBA.

     Další informace o formátech souborů dokumentů, které podporují makra, najdete v tématu [kombinování úprav na úrovni dokumentu VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Tuto funkci nelze použít v projektech šablon aplikace Word.

2. Ujistěte se, že kód VBA v dokumentu může běžet bez výzvy uživateli, aby povolil makra. Můžete důvěřovat kódu VBA pro spuštění přidáním umístění projektu Office do seznamu důvěryhodných umístění v nastavení centra zabezpečení pro Word nebo Excel.

3. Přidejte člena, který chcete zpřístupnit pro jazyk VBA, do veřejné třídy v projektu a deklarujte nového člena jako **veřejné**.

4. Použijte následující <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy a <xref:Microsoft.VisualBasic.ComClassAttribute> pro třídu, kterou vystavujete do jazyka VBA. Tyto atributy nastaví třídu jako viditelnou pro VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Přepište metodu **GetAutomationObject** třídy hostitelské položky v projektu tak, aby vracela instanci třídy, kterou vystavujete do jazyka VBA. Následující příklad kódu předpokládá, že zveřejňujete třídu s názvem `DocumentUtilities` do jazyka VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. V aplikaci otevřete Návrhář dokumentu (pro Word) nebo listu (pro Excel) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. V okně **vlastnosti** vyberte vlastnost **ReferenceAssemblyFromVbaProject** a změňte hodnotu na **true**.

    > [!NOTE]
    > Pokud sešit nebo dokument ještě neobsahuje kód VBA nebo pokud kód VBA v dokumentu není důvěryhodný ke spuštění, zobrazí se při nastavování vlastnosti **ReferenceAssemblyFromVbaProject** na **hodnotu true** chybová zpráva. Je to proto, že Visual Studio nemůže v této situaci upravovat projekt VBA v dokumentu.

8. Ve zprávě, která se zobrazí, klikněte na **OK** . Tato zpráva vás provede tím, že pokud přidáte kód VBA do sešitu nebo dokumentu, ze kterého spouštíte projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kód VBA bude při příštím sestavení projektu ztracen. Důvodem je, že dokument ve výstupní složce sestavení je přepsán při každém sestavení projektu.

     V tomto okamžiku Visual Studio nakonfiguruje projekt tak, aby projekt VBA mohl zavolat do sestavení. Visual Studio také přidá metodu s názvem `GetManagedClass` do projektu VBA. Tuto metodu můžete zavolat z libovolného místa v projektu VBA pro přístup ke třídě, kterou jste vystavili v jazyce VBA.

9. Sestavte projekt.

## <a name="see-also"></a>Viz také
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Návod: volání kódu z jazyka VBA v projektu Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Postupy: vystavení kódu pro jazyk VBA ve Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)

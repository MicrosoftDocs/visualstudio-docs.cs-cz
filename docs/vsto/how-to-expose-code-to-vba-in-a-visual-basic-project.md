---
title: 'Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e4bc9f4227c11f8e34838a2785b27da62a0a6b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839645"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic
  Můžete zpřístupnit v kódu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu jazyka Visual Basic pro kód Applications (VBA) Pokud chcete, aby dva typy kódu komunikovat mezi sebou.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Proces jazyka Visual Basic se liší od Vizuálu C# procesu. Další informace najdete v tématu [postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Proces se liší pro kód ve třídě položku hostitele, než je pro kód v jiné třídy:  
  
- [Vystavení kódu v třídě položky hostitele](#HostItemCode)  
  
- [Vystavení kódu, který není ve třídě položky hostitele](#NonHostItem)  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak VSTO volejte I: kódu z jazyka VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Vystavení kódu v třídě položky hostitele  
 Chcete-li povolit kód VBA pro volání ve třídě položku hostitele kódu jazyka Visual Basic, nastavte **EnableVbaCallers** vlastnost položky hostitele **True**.  
  
 Názorný postup ukazuje, jak vystavit metodu třídy položku hostitele a následně ji zavolat z jazyka VBA, naleznete v tématu [návod: volání kódu z jazyka VBA v projektu jazyka Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Další informace o hostitelských položkách naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Vystavení kódu v položce hostitele pro jazyk VBA  
  
1.  Otevřete nebo vytvořte úrovni dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, který je založen na dokument aplikace Word, Excelový sešit nebo šablonu v Excelu, který podporuje makra a kód VBA, který již obsahuje.  
  
     Další informace o formátech soubor dokumentu, které podporují makra najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Tuto funkci nelze použít v projektech aplikace Word šablony.  
  
2.  Ujistěte se, že kód VBA v dokumentu může spustit bez výzvy pro uživatele povolit makra. VBA kód ke spuštění tak, že přidáte do seznamu důvěryhodných umístění v nastavení Centra zabezpečení pro aplikaci Word nebo Excel umístění projektu Office, kterému můžete důvěřovat.  
  
3.  Přidejte metodu, vlastnost nebo událost, kterou chcete zpřístupnit pro jazyk VBA na jednu z tříd položek hostitele ve vašem projektu a deklarace nového člena jako **veřejné**. Název třídy, závisí na aplikaci:  
  
    -   V textovém má název třída hostitele položek projektu, `ThisDocument` ve výchozím nastavení.  
  
    -   V projektu aplikace Excel, jsou položky třídy hostitele s názvem `ThisWorkbook`, `Sheet1`, `Sheet2`, a `Sheet3` ve výchozím nastavení.  
  
4.  Nastavte **EnableVbaCallers** vlastnosti pro položku hostitele má **True**. Tato vlastnost je k dispozici v **vlastnosti** okno, když je položka hostitele v Návrháři otevřený.  
  
     Po nastavení této vlastnosti sady Visual Studio automaticky nastaví **ReferenceAssemblyFromVbaProject** vlastnost **True**.  
  
    > [!NOTE]  
    >  Pokud sešit nebo dokument už neobsahuje kód VBA, nebo pokud kód VBA v dokumentu není důvěryhodný pro spuštění, zobrazí se chybová zpráva při nastavení **EnableVbaCallers** vlastnost **True**. Je to proto, že Visual Studio nelze upravit projektu VBA v dokumentu v této situaci.  
  
5.  Klikněte na tlačítko **OK** ve zprávě, která se zobrazí. Tato zpráva se upozorní, že přidáte kód VBA do sešitu nebo dokumentu při spouštíte projekt z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kód VBA budou ztraceny při příštím sestavení projektu. Je to proto, že dokument ve výstupní složce sestavení je přepsána pokaždé, když se sestavení projektu.  
  
     V tomto okamžiku sady Visual Studio nastaví projekt tak, aby projekt VBA může volat do sestavení. Visual Studio také přidává vlastnost s názvem `CallVSTOAssembly` k `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, nebo `Sheet3` modulu v projektu VBA. Tuto vlastnost můžete použít pro přístup k veřejné členy třídy, která je vystavena VBA.  
  
6.  Sestavte projekt.  
  
##  <a name="NonHostItem"></a> Vystavení kódu, který není ve třídě položky hostitele  
 Povolit kód VBA pro volání kódu jazyka Visual Basic, který není ve třídě položku hostitele, upravte kód tak, aby byl viditelný pro jazyk VBA.  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Chcete-li zveřejnit kód, který není ve třídě položku hostitele pro jazyk VBA  
  
1.  Otevřete nebo vytvořte úrovni dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, který je založen na dokument aplikace Word, Excelový sešit nebo šablonu v Excelu, který podporuje makra a kód VBA, který již obsahuje.  
  
     Další informace o formátech soubor dokumentu, které podporují makra najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Tuto funkci nelze použít v projektech aplikace Word šablony.  
  
2.  Ujistěte se, že kód VBA v dokumentu může spustit bez výzvy pro uživatele povolit makra. VBA kód ke spuštění tak, že přidáte do seznamu důvěryhodných umístění v nastavení Centra zabezpečení pro aplikaci Word nebo Excel umístění projektu Office, kterému můžete důvěřovat.  
  
3.  Přidat člena, který chcete zpřístupnit pro jazyk VBA veřejnou třídu ve vašem projektu a deklarace nového člena jako **veřejné**.  
  
4.  Použijte následující <xref:System.Runtime.InteropServices.ComVisibleAttribute> a <xref:Microsoft.VisualBasic.ComClassAttribute> atributy do třídy, které jsou vystaveny pro jazyk VBA. Tyto atributy zviditelnit třídy pro jazyk VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Přepsat **GetAutomationObject** metoda třídy položku hostitele ve vašem projektu a vrátit instanci třídy, které jsou vystaveny pro jazyk VBA. Následující příklad kódu předpokládá, že jsou vystaveny třídu s názvem `DocumentUtilities` pro jazyk VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Otevření dokumentu (pro aplikaci Word) nebo Návrhář tabulky (Excel) v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  V **vlastnosti** okna, vyberte **ReferenceAssemblyFromVbaProject** vlastnost a změňte hodnotu na **True**.  
  
    > [!NOTE]  
    >  Pokud sešit nebo dokument už neobsahuje kód VBA, nebo pokud kód VBA v dokumentu není důvěryhodný pro spuštění, zobrazí se chybová zpráva při nastavení **ReferenceAssemblyFromVbaProject** vlastnost **True** . Je to proto, že Visual Studio nelze upravit projektu VBA v dokumentu v této situaci.  
  
8.  Klikněte na tlačítko **OK** ve zprávě, která se zobrazí. Tato zpráva se upozorní, že přidáte kód VBA do sešitu nebo dokumentu při spouštíte projekt z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kód VBA budou ztraceny při příštím sestavení projektu. Je to proto, že dokument ve výstupní složce sestavení je přepsána pokaždé, když se sestavení projektu.  
  
     V tomto okamžiku sady Visual Studio nastaví projekt tak, aby projekt VBA může volat do sestavení. Visual Studio také přidá metodu s názvem `GetManagedClass` do projektu VBA. Tuto metodu lze volat z libovolného místa v projektu VBA pro přístup ke třídě, která je vystavena VBA.  
  
9. Sestavte projekt.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Návod: Volání kódu z jazyka VBA v projektu jazyka Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  
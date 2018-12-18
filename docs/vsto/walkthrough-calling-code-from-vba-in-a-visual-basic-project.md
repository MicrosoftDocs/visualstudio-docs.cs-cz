---
title: 'Návod: Volání kódu z jazyka VBA v projektu jazyka Visual Basic'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd766e8ce1896c0b53d32cbe3f4174da5bc934d7
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808934"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Návod: Volání kódu z jazyka VBA v projektu jazyka Visual Basic
  Tento návod ukazuje, jak volat metodu v přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Word v prostředí Visual Basic pro kód Applications (VBA) v dokumentu. Postup zahrnuje tři základní kroky: Přidejte metodu k `ThisDocument` hostování třída položek, zveřejňují metodu pro kód VBA a poté zavolejte metodu z kód VBA v dokumentu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 I když tento návod používá slovo konkrétně podle návodu jsme vám ukázali konceptů platí také pro projekty na úrovni dokumentu pro Excel.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření dokumentu, který obsahuje kód VBA.  
  
-   Důvěřující umístění dokumentu pomocí Centra zabezpečení v aplikaci Word.  
  
-   Přidání metody do `ThisDocument` hostovat třída položek.  
  
-   Vystavení metodu pro kód VBA.  
  
-   Volání metody z jazyka VBA kód.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-a-document-that-contains-vba-code"></a>Vytvoření dokumentu, který obsahuje kód VBA  
 Prvním krokem je vytvoření dokumentu s podporou maker, která obsahuje jednoduché – makro VBA. Dokument musí obsahovat projekt VBA, než vytvoříte projekt sady Visual Studio, který je založen na tento dokument. V opačném případě sady Visual Studio nelze změnit projekt VBA umožňující kód VBA, chcete-li volat vlastního nastavení sestavení.  
  
 Pokud už máte dokument, který obsahuje kód VBA, který chcete použít, můžete tento krok přeskočit.  
  
### <a name="to-create-a-document-that-contains-vba-code"></a>Vytvoření dokumentu, který obsahuje kód VBA  
  
1.  Spuštění aplikace Word.  
  
2.  Uložit aktivní dokument jako slovo **dokument s podporou maker (\*DOCM)** s názvem **DocumentWithVBA**. Uložte ho na místě, například na plochu.  
  
3.  Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
    > [!NOTE]  
    >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  V **kód** klikněte na možnost **jazyka Visual Basic**.  
  
     Otevře se Editor jazyka Visual Basic.  
  
5.  V **projektu** okna, dvakrát klikněte na panel **ThisDocument**.  
  
     V souboru kódu `ThisDocument` objektu se otevře.  
  
6.  Přidejte následující kód VBA do souboru kódu. Tento kód definuje jednoduchou funkci, která nemá žádný účinek. Jediným účelem této funkce je zajistit, že existuje projekt VBA v dokumentu. Toto je nezbytné pro pozdější kroky v tomto názorném postupu.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Dokument uložte a ukončete Word.  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Nyní můžete vytvořit projekt úrovni dokumentu pro Word, který používá s podporou maker dokument, který jste vytvořili dříve.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**. Pokud vaše rozhraní IDE nastaveno pro použití vývojového nastavení jazyka Visual Basic, na **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
3.  V podokně šablony rozbalte **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  Vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte **dokument aplikace Word 2010** nebo **dokument aplikace Word 2013** projektu.  
  
6.  V **název** zadejte **CallingCodeFromVBA**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     **Visual Studio Tools for Office Project Wizard** otevře.  
  
8.  Vyberte **zkopírovat existující dokument**a v **úplnou cestu k existujícímu dokumentu** zadejte umístění **DocumentWithVBA** dokument, který jste vytvořili dříve . Pokud používáte s podporou maker dokumentu, zadejte umístění tohoto dokumentu.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **DocumentWithVBA** dokumentu v návrháři a přidá **CallingCodeFromVBA** projektu **Průzkumníka řešení**.  
  
## <a name="trust-the-location-of-the-document"></a>Důvěřujete umístění dokumentu  
 Před vystavení kódu v řešení pro kód VBA v dokumentu, musí důvěřovat VBA v dokumentu, který má spustit. Chcete-li to provést několika způsoby. V tomto návodu důvěřovat umístění dokumentu **centrum** v aplikaci Word.  
  
### <a name="to-trust-the-location-of-the-document"></a>Důvěřovat umístění dokumentu  
  
1.  Spuštění aplikace Word.  
  
2.  Klikněte na tlačítko **souboru** kartu.  
  
3.  Klikněte na tlačítko **možnosti v aplikaci Word** tlačítko.  
  
4.  V podokně kategorie, klikněte na tlačítko **centrum**.  
  
5.  V podokně podrobností klikněte na tlačítko **nastavení Centra zabezpečení**.  
  
6.  V podokně kategorie, klikněte na tlačítko **důvěryhodná umístění**.  
  
7.  V podokně podrobností klikněte na tlačítko **přidat nové umístění**.  
  
8.  V **Microsoft Office důvěryhodné umístění** dialogové okno, přejděte do složky, která obsahuje **CallingCodeFromVBA** projektu.  
  
9. Vyberte **podsložky tohoto umístění jsou také důvěryhodné**.  
  
10. V **Microsoft Office důvěryhodné umístění** dialogové okno, klikněte na tlačítko **OK**.  
  
11. V **centrum** dialogové okno, klikněte na tlačítko **OK**.  
  
12. V **možnosti v aplikaci Word** dialogové okno, klikněte na tlačítko **OK**.  
  
13. Ukončete aplikaci Word.  
  
## <a name="add-a-method-to-the-thisdocument-class"></a>Přidejte metodu ThisDocument – třída  
 Teď, když je nastavení projektu VBA, přidejte metodu k `ThisDocument` hostovat třída položek, které můžete volat z jazyka VBA kód.  
  
### <a name="to-add-a-method-to-the-thisdocument-class"></a>Přidání metody ThisDocument – třída  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument.vb**a potom klikněte na tlačítko **zobrazit kód**.  
  
     **ThisDocument.vb** soubor se otevře v editoru kódu.  
  
2.  Přidejte následující metodu do `ThisDocument` třídy. Tato metoda vytvoří tabulku se dvěma řádky a dva sloupce na začátku dokumentu. Parametry zadejte text, který se zobrazí v prvním řádku. Později v tomto návodu bude tuto metodu volat z kódu jazyka VBA v dokumentu.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Sestavte projekt.  
  
## <a name="expose-the-method-to-vba-code"></a>Vystavit metodu pro kód VBA  
 Zveřejnit `CreateTable` metodu pro kód VBA v dokumentu, nastavte **EnableVbaCallers** vlastnost `ThisDocument` položka hostitele na **True**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>Vystavit metodu pro kód VBA  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **ThisDocument.vb**.  
  
     **DocumentWithVBA** soubor se otevře v návrháři.  
  
2.  V **vlastnosti** okna, vyberte **EnableVbaCallers** vlastnost a změňte hodnotu na **True**.  
  
3.  Klikněte na tlačítko **OK** ve zprávě, která se zobrazí.  
  
4.  Sestavte projekt.  
  
## <a name="call-the-method-from-vba-code"></a>Volání metody z jazyka VBA kód  
 Nyní můžete volat `CreateTable` metodu z kód VBA v dokumentu.  
  
> [!NOTE]  
>  V tomto názorném postupu přidáte kód VBA v dokumentu během ladění projektu. Kód VBA, který přidáte do tohoto dokumentu se přepíše při příštím sestavení projektu, protože Visual Studio nahradí kopii dokumentu ze složky projektu hlavní dokument ve výstupní složce sestavení. Pokud chcete uložit kód VBA, zkopírujte jej do dokumentu ve složce projektu. Další informace najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>Volat metodu z jazyka VBA kód  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Na **Developer** kartě **kód** klikněte na možnost **jazyka Visual Basic**.  
  
     Otevře se Editor jazyka Visual Basic.  
  
3.  Na **vložit** nabídky, klikněte na tlačítko **modulu**.  
  
4.  Přidejte následující kód do nového modulu.  
  
     Tento kód volá `CreateTable` metoda v vlastního nastavení sestavení. Makro přistupuje pomocí této metody `CallVSTOAssembly` vlastnost `ThisDocument` objektu. Tato vlastnost se vygeneroval automaticky při nastavení **EnableVbaCallers** vlastnost dříve v tomto návodu.  
  
    ```vb  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Stisknutím klávesy **F5**.  
  
6.  Ověřte, že nová tabulka byl přidán do dokumentu.  
  
7.  Ukončete Word bez uložení změn.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o volání kódu v řešeních pro systém Office z jazyka VBA v těchto tématech:  
  
-   Volání kódu v přizpůsobení jazyka Visual C# z jazyka VBA. Tento proces se liší od procesu jazyka Visual Basic. Další informace najdete v tématu [návod: volání kódu z jazyka VBA v aplikaci Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Volání kódu v doplňku VSTO z jazyka VBA. Další informace najdete v tématu [návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Viz také:  
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Návod: Volání kódu z jazyka VBA v aplikaci Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  
---
title: 'Návod: volání kódu z jazyka VBA v projektu Visual Basic'
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad50ed0f55a148a05c0fedc6fe0ccb0dd5b890b9
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298265"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Návod: volání kódu z jazyka VBA v projektu Visual Basic
  Tento návod ukazuje, jak volat metodu v přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word z kódu jazyk Visual Basic for Application (VBA) v dokumentu. Postup zahrnuje tři základní kroky: Přidání metody do `ThisDocument` třídy hostitelské položky, vystavení metody pro kód VBA a následné volání metody z kódu VBA v dokumentu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 I když tento návod používá slovo konkrétně, koncepce znázorněné v tomto návodu se vztahují také na projekty na úrovni dokumentu v Excelu.

 Tento návod znázorňuje následující úlohy:

- Vytvoření dokumentu, který obsahuje kód VBA.

- Důvěřuje umístění dokumentu pomocí centra zabezpečení ve Wordu.

- Přidání metody do `ThisDocument` třídy položky hostitele.

- Vystavení metody pro kód VBA.

- Volání metody z kódu VBA.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Vytvoření dokumentu, který obsahuje kód VBA
 Prvním krokem je vytvoření dokumentu s povoleným makrem, který obsahuje jednoduché makro VBA. Aby bylo možné vytvořit projekt sady Visual Studio, který je založen na tomto dokumentu, musí dokument obsahovat projekt VBA. V opačném případě Visual Studio nemůže upravit projekt VBA, aby kód VBA mohl volat do sestavení vlastního nastavení.

 Pokud již máte dokument, který obsahuje kód VBA, který chcete použít, můžete tento krok přeskočit.

### <a name="to-create-a-document-that-contains-vba-code"></a>Vytvoření dokumentu, který obsahuje kód VBA

1. Spusťte aplikaci Word.

2. Uloží aktivní dokument jako wordový **dokument s podporou maker ( \* . docm)** s názvem **DocumentWithVBA**. Uložte ho do vhodného umístění, jako je například plocha.

3. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Ve skupině **kódu** klikněte na **Visual Basic**.

     Otevře se Visual Basic Editor.

5. V okně **projektu** poklikejte na **ThisDocument**.

     Otevře se soubor s kódem pro daný `ThisDocument` objekt.

6. Do souboru kódu přidejte následující kód VBA. Tento kód definuje jednoduchou funkci, která neprovede žádnou akci. Jediným účelem této funkce je zajistit, aby v dokumentu existoval projekt VBA. To je nutné pro pozdější kroky v tomto návodu.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Uložte dokument a ukončete aplikaci Word.

## <a name="create-the-project"></a>Vytvoření projektu
 Nyní můžete vytvořit projekt na úrovni dokumentu pro aplikaci Word, který používá dokument s podporou maker, který jste vytvořili dříve.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**. Pokud je vaše rozhraní IDE nastaveno na použití Visual Basic vývojové nastavení, v nabídce **soubor** klikněte na **Nový projekt**.

3. V podokně šablony rozbalte položku **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

4. Vyberte uzel **Doplňky pro Office** .

5. V seznamu šablon projektu vyberte **dokument aplikace word 2010** nebo **dokument aplikace Word 2013** .

6. Do pole **název** zadejte **CallingCodeFromVBA**.

7. Klikněte na **OK**.

     Otevře se **Průvodce projektem Visual Studio Tools for Office** .

8. Vyberte možnost **zkopírovat existující dokument**a v poli **Úplná cesta k existujícímu dokumentu** zadejte umístění dokumentu **DocumentWithVBA** , který jste vytvořili dříve. Pokud používáte vlastní dokument s podporou maker, určete místo toho umístění tohoto dokumentu.

9. Klikněte na **Finish** (Dokončit).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře dokument **DocumentWithVBA** v návrháři a přidá projekt **CallingCodeFromVBA** do **Průzkumník řešení**.

## <a name="trust-the-location-of-the-document"></a>Důvěřovat umístění dokumentu
 Předtím, než můžete vystavit kód ve vašem řešení pro kód VBA v dokumentu, je nutné v dokumentu pro spuštění důvěřovat jazyku VBA. Existuje několik způsobů, jak to udělat. V tomto návodu důvěřujete umístění dokumentu v **Centru zabezpečení** ve Wordu.

### <a name="to-trust-the-location-of-the-document"></a>Chcete-li důvěřovat umístění dokumentu

1. Spusťte aplikaci Word.

2. Klikněte na kartu **soubor** .

3. Klikněte na tlačítko **Možnosti aplikace Word** .

4. V podokně kategorie klikněte na **Centrum zabezpečení**.

5. V podokně podrobností klikněte na **Nastavení centra zabezpečení**.

6. V podokně kategorie klikněte na možnost **důvěryhodná umístění**.

7. V podokně podrobností klikněte na **Přidat nové umístění**.

8. V dialogovém okně **systém Microsoft Office důvěryhodné umístění** přejděte do složky, která obsahuje projekt **CallingCodeFromVBA** .

9. Vybrat **podsložky tohoto umístění jsou také důvěryhodné**.

10. V dialogovém okně **systém Microsoft Office důvěryhodné umístění** klikněte na tlačítko **OK**.

11. V dialogovém okně **Centrum zabezpečení** klikněte na tlačítko **OK**.

12. V dialogovém okně **Možnosti aplikace Word** klikněte na tlačítko **OK**.

13. Ukončete aplikaci Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Přidání metody do třídy ThisDocument
 Teď, když je projekt VBA nastavený, přidejte metodu do `ThisDocument` třídy hostitelské položky, kterou můžete volat z kódu VBA.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>Přidání metody do třídy ThisDocument

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ThisDocument. vb**a pak klikněte na **Zobrazit kód**.

     V editoru kódu se otevře soubor **ThisDocument. vb** .

2. Do třídy přidejte následující metodu `ThisDocument` . Tato metoda vytvoří tabulku se dvěma řádky a dvěma sloupci na začátku dokumentu. Parametry určují text, který se zobrazí na prvním řádku. Později v tomto návodu budete volat tuto metodu z kódu VBA v dokumentu.

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. Sestavte projekt.

## <a name="expose-the-method-to-vba-code"></a>Vystavení metody pro kód VBA
 K vystavení `CreateTable` metody pro kód VBA v dokumentu nastavte vlastnost **EnableVbaCallers** pro `ThisDocument` položku hostitele na **true**.

### <a name="to-expose-the-method-to-vba-code"></a>Vystavení metody pro kód VBA

1. V **Průzkumník řešení**dvakrát klikněte na **ThisDocument. vb**.

     Otevře se soubor **DocumentWithVBA** v návrháři.

2. V okně **vlastnosti** vyberte vlastnost **EnableVbaCallers** a změňte hodnotu na **true**.

3. Ve zprávě, která se zobrazí, klikněte na **OK** .

4. Sestavte projekt.

## <a name="call-the-method-from-vba-code"></a>Volání metody z kódu VBA
 Nyní můžete volat `CreateTable` metodu z kódu VBA v dokumentu.

> [!NOTE]
> V tomto návodu přidáte kód VBA do dokumentu během ladění projektu. Kód VBA, který přidáte do tohoto dokumentu, bude při příštím sestavení projektu přepsán, protože Visual Studio nahradí dokument ve výstupní složce sestavení kopií dokumentu z hlavní složky projektu. Pokud chcete kód VBA uložit, můžete ho zkopírovat do dokumentu ve složce projektu. Další informace najdete v tématu [Kombinování přizpůsobení na úrovni VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Volání metody z kódu jazyka VBA

1. Stisknutím klávesy **F5** spusťte projekt.

2. Na kartě **vývojář** ve skupině **kód** klikněte na **Visual Basic**.

     Otevře se Visual Basic Editor.

3. V nabídce **Vložit** klikněte na **modul**.

4. Do nového modulu přidejte následující kód.

     Tento kód volá `CreateTable` metodu v sestavení přizpůsobení. Makro přistupuje k této metodě pomocí `CallVSTOAssembly` vlastnosti `ThisDocument` objektu. Tato vlastnost se automaticky vygenerovala při nastavení vlastnosti **EnableVbaCallers** dříve v tomto návodu.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Stiskněte klávesu **F5**.

6. Ověřte, že se do dokumentu přidala nová tabulka.

7. Ukončí aplikaci Word bez uložení změn.

## <a name="next-steps"></a>Další kroky
 Další informace o volání kódu v řešeních pro systém Office z jazyka VBA najdete v těchto tématech:

- Zavolejte kód v přizpůsobení Visual C# z VBA. Tento proces se liší od procesu Visual Basic. Další informace naleznete v tématu [Návod: volání kódu z jazyka VBA v projektu jazyka Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

- Volání kódu v doplňku VSTO z jazyka VBA. Další informace naleznete v tématu [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Viz také
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Postupy: vystavení kódu pro jazyk VBA ve Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Návod: volání kódu z jazyka VBA ve Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)

---
title: 'Návod: Importujte oblasti formuláře navržené v aplikaci Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 413d2fed56da809b2fdb8c1fad867818e0cce010
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903514"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Návod: Importujte oblasti formuláře navržené v aplikaci Outlook
  Tento návod ukazuje, jak návrh oblasti formuláře v aplikaci Microsoft Office Outlook a pak pomocí import oblasti formuláře do projektu doplňku VSTO pro Outlook **novou oblast formuláře** průvodce. Návrh oblasti formuláře v Outlooku umožňuje přidat nativní ovládací prvky aplikace Outlook k oblasti formuláře, který svázat data Outlooku. Jakmile dokončíte import oblasti formuláře, můžete zpracovávat události každého ovládacího prvku.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Návrh oblasti formuláře pomocí návrhářem oblasti formuláře v Outlooku.  
  
- Import oblasti formuláře do projektu doplňku VSTO v Outlooku.  
  
- Zpracování událostí ovládacích prvků na oblast formuláře.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] nebo [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak oblasti formuláře Outlooku I: vytvoření pomocí sady Visual Studio 2008?](http://go.microsoft.com/fwlink/?LinkID=130305).  
## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Návrh oblasti formuláře pomocí návrhářem oblasti formuláře v aplikaci Outlook  
 V tomto kroku navrhnete oblasti formuláře v Outlooku. Budete pak uložení oblasti formuláře k umístění služby – hledání tak, aby je bylo možné importovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Tato oblast formuláře příklad zcela nahrazují formuláři obvyklé úlohy. Poskytuje způsob, jak sledovat průběh všech úloh, které musíte splnit, předtím, než hlavního úkolu můžete provést (požadované úkoly). Oblast formuláře zobrazí seznam požadované úkoly a zobrazí stav dokončení pro každý úkol v seznamu. Uživatele můžete přidat do seznamu úkolů a je odebrat. Můžete aktualizovat také stav dokončení každé úlohy.  
  
### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Chcete-li návrh oblasti formuláře pomocí návrhářem oblasti formuláře v aplikaci Outlook  
  
1.  Spusťte aplikaci Microsoft Office Outlook.  
  
2.  V aplikaci Outlook na **Developer** klikněte na tlačítko **návrhu formuláře**. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  V **návrhu formuláře** klikněte **úloh**a potom klikněte na tlačítko **otevřít**.  
  
4.  V aplikaci Outlook na **Developer** kartě **návrhu** klikněte na možnost **novou oblast formuláře**.  
  
     Otevře novou oblast formuláře. Pokud **pole výběru** nezobrazí, klikněte na tlačítko **pole výběru** v **nástroje** skupiny.  
  
5.  Přetáhněte **subjektu** pole a **dokončeno %** pole z **pole výběru** na oblast formuláře.  
  
6.  V **nástroje** klikněte na možnost **ovládací prvky** otevřít **nástrojů**.  
  
7.  Přetáhněte popisek z **nástrojů** na oblast formuláře. Umístit popisek pod **subjektu** a **dokončeno %** pole.  
  
8.  Klikněte pravým tlačítkem na popisek a potom klikněte na tlačítko **Upřesnit vlastnosti**.  
  
9. V **vlastnosti** okno, nastaveno **titulek** vlastnost **tento úkol závisí na následujících úloh**, nastavte **šířka** vlastnost **200**a potom klikněte na tlačítko **použít**.  
  
10. Přetáhněte ovládací prvek ListBox z **nástrojů** na oblast formuláře. Umístěte pole se seznamem pod **tento úkol závisí na následujících úloh** popisek.  
  
11. Vyberte seznam, který jste právě přidali.  
  
12. V **vlastnosti** okno, nastavte **šířka** k **300**a potom klikněte na tlačítko **použít**.  
  
13. Přetáhněte popisek z **nástrojů** na oblast formuláře. Umístěte popisek pod pole se seznamem.  
  
14. Vyberte popisek, který jste právě přidali.  
  
15. V **vlastnosti** okno, nastaveno **titulek** vlastnost **vyberte úkol, který chcete přidat do seznamu úkolů, závislé**, nastavte **šířku** Vlastnost **200**a potom klikněte na tlačítko **použít**.  
  
16. Přetáhněte ovládací prvek pole se seznamem z **nástrojů** na oblast formuláře. Umístěte pole se seznamem pod **vyberte úlohu přidání na seznam závislých úloh** popisek.  
  
17. Vyberte pole se seznamem, který jste právě přidali.  
  
18. V **vlastnosti** okno, nastavte **šířka** vlastnost **300**a potom klikněte na tlačítko **použít**.  
  
19. Přetáhněte z ovládacího prvku CommandButton **nástrojů** na oblast formuláře. Umístění příkazového tlačítka vedle pole se seznamem.  
  
20. Vyberte příkazové tlačítko, které jste právě přidali.  
  
21. V **vlastnosti** okno, nastavte **název** k **AddDependentTask**, nastavte **titulek** k **přidat závislé úkol**nastavte **šířka** k **100**a potom klikněte na tlačítko **použít**.  
  
22. V **pole výběru**, klikněte na tlačítko **nový**.  
  
23. V **nové pole** dialogovém okně **hiddenField** v **název** pole a potom klikněte na tlačítko **OK**.  
  
24. Přetáhněte **hiddenField** pole z **pole výběru** na oblast formuláře.  
  
25. V **vlastnosti** okno, nastavte **Visible** k **0 - NEPRAVDA**a potom klikněte na tlačítko **použít**.  
  
26. V Outlooku na **Developer** kartě **návrhu** klikněte na možnost **Uložit** tlačítko a pak klikněte na tlačítko **uložit oblasti formuláře jako**.  
  
     Název oblasti formuláře **TaskFormRegion** a uložte ho do místního adresáře v počítači.  
  
     Aplikace Outlook ukládá oblasti formuláře jako úložiště formulářů Outlooku (*.ofs*) soubor. Oblast formuláře je uložen pod názvem *TaskFormRegion.ofs*.  
  
27. Ukončete aplikaci Outlook.  
  
## <a name="create-a-new-outlook-add-in-project"></a>Vytvoření nového projektu doplňku aplikace Outlook  
 V tomto kroku vytvoříte projekt doplňku VSTO v Outlooku. Později v tomto návodu budete importovat oblasti formuláře do projektu.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Outlook  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření projektu doplňku VSTO pro Outlook s názvem **TaskAddIn**.  
  
2.  V **nový projekt** dialogu **vytvořit adresář pro řešení**.  
  
3.  Uložte projekt do výchozí adresář projektu.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="import-the-form-region"></a>Import oblasti formuláře  
 Můžete importovat oblasti formuláře navržené v aplikaci Outlook do projektu doplňku VSTO pro Outlook s použitím **novou oblast formuláře Outlooku** průvodce.  
  
### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Pro import oblasti formuláře do projektu doplňku VSTO pro Outlook  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem **TaskAddIn** projektu, přejděte na **přidat**a potom klikněte na **nová položka**.  
  
2.  V **šablony** vyberte **oblast formuláře Outlooku**, pojmenujte soubor **TaskFormRegion**a potom klikněte na tlačítko **přidat**.  
  
     **Oblasti formuláře NewOutlook** spustí se průvodce.  
  
3.  Na **vyberte způsob vytvoření oblasti formuláře** klikněte na **importovat úložiště formulářů Outlooku (.ofs) soubor**a potom klikněte na tlačítko **Procházet**.  
  
4.  V **existující umístění souboru oblasti formuláře Outlooku** dialogové okno, přejděte do umístění *TaskFormRegion.ofs*vyberte **TaskFormRegion.ofs**, klikněte na tlačítko **Otevřít**a potom klikněte na tlačítko **Další**.  
  
5.  Na **výběr typu oblasti formuláře chcete vytvořit** klikněte na **nahradit všechno**a potom klikněte na tlačítko **Další**.  
  
     A *nahradit všechno* oblasti formuláře nahradí celý formulář aplikace Outlook. Další informace o oblasti formuláře typu naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
6.  Na **zadání popisného textu a výběr předvoleb zobrazení** klikněte na **Další**.  
  
7.  Na **identifikování tříd zpráv, které budou zobrazovat tuto oblast formuláře** stránku, **které vlastní třídy zpráv budou zobrazovat tuto oblast formuláře** zadejte **IPM. Task.TaskFormRegion**a potom klikněte na tlačítko **Dokončit**.  
  
     A *TaskFormRegion.cs* nebo *TaskFormRegion.vb* přidá soubor do projektu.  
  
## <a name="handle-the-events-of-controls-on-the-form-region"></a>Zpracování událostí ovládacích prvků na oblast formuláře  
 Teď, když máte oblasti formuláře v projektu, můžete přidat kód, který zpracovává `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` událost tlačítka, které jste přidali do oblasti formuláře v Outlooku.  
  
 Také, přidejte kód pro <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> událost, která aktualizuje ovládacích prvků na oblast formuláře, když se oblast formuláře zobrazí.  
  
### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Zpracování událostí ovládacích prvků na oblast formuláře  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na *TaskFormRegion.cs* nebo *TaskFormRegion.vb*a potom klikněte na tlačítko **zobrazit kód**.  
  
    *TaskFormRegion.cs* nebo *TaskFormRegion.vb* otevře v editoru kódu.  
  
2. Přidejte následující kód, který `TaskFormRegion` třídy. Tento kód se naplní pole se seznamem na oblast formuláře s řádkem předmětu jednotlivých úkolů ve složce úkolů Outlooku.  
  
    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]  
  
3. Přidejte následující kód, který `TaskFormRegion` třídy. Tento kód provede následující:  
  
   - Vyhledá `Microsoft.Office.Interop.Outlook.TaskItem` ve složce úlohy voláním `FindTaskBySubjectName` pomocnou metodu a předáním subjektu vyberte požadovanou úlohu. Přidáte `FindTaskBySubjectName` pomocnou metodu v dalším kroku.  
  
   - Přidá `Microsoft.Office.Interop.Outlook.TaskItem.Subject` a `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` hodnoty pro pole se seznamem úkolů závislé.  
  
   - Přidá předmět úkolu do skryté pole na oblast formuláře. Skryté pole tyto hodnoty ukládá jako součást položky aplikace Outlook.  
  
     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]  
  
4. Přidejte následující kód, který `TaskFormRegion` třídy. Tento kód poskytuje metodu helper `FindTaskBySubjectName` , která byla popsána v předchozím kroku.  
  
    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]  
  
5. Přidejte následující kód, který `TaskFormRegion` třídy. Tento kód provede následující:  
  
   - Aktualizuje seznam na oblast formuláře zobrazí aktuální stav dokončení každé úlohy závislé.  
  
   - Analyzuje skryté textového pole a získat předmět každý úkol závisí. Poté vyhledá každá `Microsoft.Office.Interop.Outlook.TaskItem` v *úlohy* složky voláním `FindTaskBySubjectName` pomocnou metodu a předáním předmětu jednotlivých úkolů.  
  
   - Přidá `Microsoft.Office.Interop.Outlook.TaskItem.Subject` a `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` hodnoty pro pole se seznamem úkolů závislé.  
  
     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]  
  
6. Nahradit `TaskFormRegion_FormRegionShowing` obslužné rutiny události s následujícím kódem. Tento kód provede následující:  
  
   - Naplní pole se seznamem na oblast formuláře s předměty úkolů po zobrazení oblasti formuláře.  
  
   - Volání `RefreshTaskListBox` pomocnou metodu, když se objeví oblast formuláře. Zobrazí všechny závislé úlohy, které byly přidány do seznamu, když položka byl dříve otevřen.  
  
     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]  
  
## <a name="test-the-outlook-form-region"></a>Testovací oblast formuláře Outlooku  
 Pokud chcete otestovat oblasti formuláře, přidání úkolů do seznamu požadované úkoly v oblasti formuláře. Aktualizovat stav dokončení požadovaných součástí úlohy a potom zobrazit stav aktualizované dokončení úkolu v seznamu úloh požadovaných součástí.  
  
### <a name="to-test-the-form-region"></a>K otestování oblasti formuláře  
  
1.  Stisknutím klávesy **F5** spusťte projekt.  
  
     Spuštění aplikace Outlook.  
  
2.  V aplikaci Outlook na **Domů** klikněte na tlačítko **nové položky**a potom klikněte na tlačítko **úloh**.  
  
3.  Ve formuláři úkolu zadejte **závislá úloha** v **subjektu** pole.  
  
4.  Na **úloh** kartu na pásu karet v **akce** klikněte na možnost **uložit a zavřít**.  
  
5.  V aplikaci Outlook na **Domů** klikněte na tlačítko **nové položky**, klikněte na tlačítko **více položek**a potom klikněte na tlačítko **zvolit formulář**.  
  
6.  V **zvolit formulář** dialogové okno, klikněte na tlačítko **TaskFormRegion**a potom klikněte na tlačítko **otevřít**.  
  
     **TaskFormRegion** se oblast formuláře zobrazí. Tento formulář nahradí formuláři celá úloha. **Vyberte úlohu přidání na seznam závislých úloh** – pole se seznamem se vyplní ostatní úlohy ve složce úlohy.  
  
7.  Ve formuláři úkolu v **subjektu** zadejte **primárního úkolu**.  
  
8.  V **vyberte úlohu přidání na seznam závislých úloh** – pole se seznamem, vyberte **závislá úloha**a potom klikněte na tlačítko **přidat závislé úkol**.  
  
     **0 % dokončeno--závislá úloha** se zobrazí v **tento úkol závisí na následujících úloh** pole se seznamem. Tento příklad ukazuje, že jste úspěšně zpracována `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` událost tlačítka.  
  
9. Uložte a zavřete **primárního úkolu** položky.  
  
10. Znovu otevřete závislé úkol v Outlooku.  
  
11. Ve formuláři závislý úkol změnit **dokončeno %** pole **50 %**.  
  
12. Na **úloh** kartu pásu karet závislé úlohy v **akce** klikněte na možnost **uložit a zavřít**.  
  
13. Znovu otevřít **primárního úkolu** položky v Outlooku.  
  
     **50 % bylo dokončeno--závislá úloha** se teď zobrazí v **tento úkol závisí na následujících úloh** pole se seznamem.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikace Outlook z těchto témat:  
  
-   Další informace o tom, jak navrhnout vzhled oblasti formuláře přetahování spravovaných ovládacích prvků na vizuálního návrháře, naleznete v tématu [návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Další informace o tom, jak přizpůsobit na pásu karet položky Outlooku, naleznete v tématu [přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
-   Další informace o způsobu přidání vlastního podokna úloh do aplikace Outlook, naleznete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Postupy: zabránění zobrazení oblasti formuláře Outlooku](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  
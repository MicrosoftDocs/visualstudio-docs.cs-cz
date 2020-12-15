---
title: 'Návod: import oblasti formuláře navržené v aplikaci Outlook'
description: Naučte se navrhovat oblast formuláře v aplikaci Microsoft Outlook a pak ji importovat do projektu doplňku VSTO aplikace Outlook pomocí Průvodce vytvořením nové oblasti formuláře.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b65502bbf29f6e0df7435f6a27d3c51e8082e41
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522672"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Návod: import oblasti formuláře navržené v aplikaci Outlook
  Tento názorný postup ukazuje návrh oblasti formuláře v aplikaci systém Microsoft Office Outlook a následné importování oblasti formuláře do projektu doplňku aplikace Outlook VSTO pomocí Průvodce vytvořením **nové oblasti formuláře** . Návrh oblasti formuláře v aplikaci Outlook umožňuje přidat nativní ovládací prvky aplikace Outlook do oblasti formuláře, která je vázána na data aplikace Outlook. Po importu oblasti formuláře můžete zpracovat události každého ovládacího prvku.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Návrh oblasti formuláře pomocí návrháře oblasti formuláře v aplikaci Outlook.

- Import oblasti formuláře do projektu doplňku aplikace Outlook VSTO.

- Zpracování událostí ovládacích prvků v oblasti formuláře.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] nebo [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]:

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Návrh oblasti formuláře pomocí návrháře oblasti formuláře v aplikaci Outlook
 V tomto kroku navrhnete oblast formuláře v aplikaci Outlook. Pak budete moct uložit oblast formuláře do snadno hledaného umístění, abyste ho mohli naimportovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Tato ukázková oblast formuláře zcela nahrazuje běžný formulář úkolu. Poskytuje způsob, jak sledovat průběh všech úloh, které musí být dokončeny, aby bylo možné provést hlavní úlohu (požadované úkoly). Oblast formuláře zobrazuje seznam požadovaných úkolů a zobrazuje stav dokončení pro každý úkol v seznamu. Uživatelé můžou přidat úkoly do seznamu a odebrat je. Můžou také aktualizovat stav dokončení jednotlivých úloh.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Návrh oblasti formuláře pomocí návrháře oblasti formuláře v aplikaci Outlook

1. Spusťte aplikaci systém Microsoft Office Outlook.

2. V Outlooku na kartě **vývojář** klikněte na **navrhnout formulář**. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. V poli **formulář návrhu** klikněte na **úloha** a pak klikněte na **otevřít**.

4. V aplikaci Outlook na kartě **vývojář** ve skupině **Návrh** klikněte na možnost **Nová oblast formuláře**.

     Otevře se nová oblast formuláře. Pokud se **výběr pole** nezobrazí, klikněte ve skupině **nástroje** na **Výběr polí** .

5. Přetáhněte pole **Předmět** a pole **dokončeno%** z **výběru pole** do oblasti formuláře.

6. Ve skupině **nástroje** klikněte na **ovládací panel nástrojů** a otevřete **sadu nástrojů**.

7. Přetáhněte popisek z **panelu nástrojů** do oblasti formuláře. Umístěte popisek pod pole **Předmět** a **dokončeno%** .

8. Klikněte pravým tlačítkem na popisek a pak klikněte na **Upřesnit vlastnosti**.

9. V okně **vlastnosti** nastavte vlastnost **Titulek** na **Tento úkol závisí na následujících úkolech**, nastavte vlastnost **Width** na **200** a potom klikněte na tlačítko **použít**.

10. Přetáhněte ovládací prvek ListBox z **panelu nástrojů** do oblasti formuláře. Umístit seznam pod **tuto úlohu závisí na následujícím popisku úkolů** .

11. Vyberte pole se seznamem, které jste právě přidali.

12. V okně **vlastnosti** nastavte možnost **Šířka** na **300** a pak klikněte na **použít**.

13. Přetáhněte popisek z **panelu nástrojů** do oblasti formuláře. Umístěte popisek pod pole seznamu.

14. Vyberte popisek, který jste právě přidali.

15. V okně **vlastnosti** nastavte vlastnost **Titulek** na **možnost vyberte úkol, který chcete přidat do seznamu závislých úloh**, nastavte vlastnost **Width** na **200** a potom klikněte na tlačítko **použít**.

16. Přetáhněte ovládací prvek ComboBox ze **sady nástrojů** do oblasti formuláře. Umístěte pole se seznamem pod rozevíracím seznamem **Vyberte úkol, který chcete přidat do seznamu popisků závislých úloh** .

17. Vyberte pole se seznamem, které jste právě přidali.

18. V okně **vlastnosti** nastavte vlastnost **Width** na **300** a potom klikněte na **použít**.

19. Přetáhněte ovládací prvek CommandButton z **panelu nástrojů** do oblasti formuláře. Umístěte příkazové tlačítko vedle pole se seznamem.

20. Vyberte příkazové tlačítko, které jste právě přidali.

21. V okně **vlastnosti** nastavte **název** na **AddDependentTask**, nastavit **Titulek** na **přidat závislý úkol**, nastavte možnost **Šířka** na **100** a pak klikněte na **použít**.

22. V okně **výběr pole** klikněte na **Nový**.

23. Do pole **název** v dialogovém okně **nové pole** zadejte **HiddenField** a pak klikněte na **OK**.

24. Přetáhněte pole **HiddenField** z **výběru pole** do oblasti formuláře.

25. V okně **vlastnosti** nastavte hodnotu **Zobrazit** na **0 – NEPRAVDA** a pak klikněte na **použít**.

26. V Outlooku na kartě **vývojář** ve skupině **Návrh** klikněte na tlačítko **Uložit** a pak klikněte na **Uložit oblast formuláře jako**.

     Pojmenujte oblast formuláře **TaskFormRegion** a uložte ji do místního adresáře v počítači.

     Aplikace Outlook uloží oblast formuláře jako soubor úložiště formuláře aplikace Outlook (*. ofs*). Oblast formuláře se uloží s názvem *TaskFormRegion. ofs*.

27. Ukončete aplikaci Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Vytvoření nového projektu doplňku pro Outlook
 V tomto kroku vytvoříte projekt doplňku VSTO pro Outlook. Později v tomto návodu budete importovat oblast formuláře do projektu.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt doplňku VSTO pro Outlook s názvem **TaskAddIn**.

2. V dialogovém okně **Nový projekt** vyberte **vytvořit adresář pro řešení**.

3. Uložte projekt do výchozího adresáře projektu.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Import oblasti formuláře
 Oblast formuláře, kterou jste navrhli v aplikaci Outlook, můžete importovat do projektu doplňku aplikace Outlook VSTO pomocí Průvodce vytvořením **nové oblasti formuláře Outlook** .

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Import oblasti formuláře do projektu doplňku VSTO pro Outlook

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt **TaskAddIn** , přejděte na **Přidat** a klikněte na **Nová položka**.

2. V podokně **šablony** vyberte možnost **oblast formuláře Outlook**, název souboru **TaskFormRegion** a pak klikněte na tlačítko **Přidat**.

     Spustí se průvodce **oblastí formuláře NewOutlook** .

3. Na stránce **Vyberte, jak chcete vytvořit oblast formuláře** , klikněte na položku **importovat soubor úložiště formuláře aplikace Outlook (. ofs)** a potom klikněte na tlačítko **Procházet**.

4. V dialogovém okně **existující umístění souboru oblasti formuláře Outlooku** přejděte do umístění *TaskFormRegion. ofs*, vyberte **TaskFormRegion. ofs**, klikněte na **otevřít** a pak klikněte na **Další**.

5. Na stránce **Vyberte typ oblasti formuláře, který chcete vytvořit** klikněte na **Nahradit vše** a pak klikněte na **Další**.

     Region *Replace-All* Form nahrazuje celý formulář aplikace Outlook. Další informace o typech oblastí formuláře najdete v tématu věnovaném [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

6. Na stránce **Zadejte popisný text a vyberte své předvolby zobrazení** klikněte na **Další**.

7. V části **Identifikujte třídy zpráv, které budou zobrazovat tuto stránku oblasti** formuláře, v poli **které vlastní třídy zpráv zobrazí toto pole formuláře** , zadejte **IPM. Task. TaskFormRegion** a potom klikněte na **Dokončit**.

     Do projektu se přidá soubor *TaskFormRegion.cs* nebo *TaskFormRegion. vb* .

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Zpracování událostí ovládacích prvků v oblasti formuláře
 Teď, když máte oblast formuláře v projektu, můžete přidat kód, který zpracovává `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` Událost tlačítka, které jste přidali do oblasti formuláře v aplikaci Outlook.

 Přidejte také kód pro <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> událost, která aktualizuje ovládací prvky v oblasti formuláře při zobrazení oblasti formuláře.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Zpracování událostí ovládacích prvků v oblasti formuláře

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na *TaskFormRegion.cs* nebo *TaskFormRegion. vb* a pak klikněte na **Zobrazit kód**.

    V editoru kódu se otevře *TaskFormRegion.cs* nebo *TaskFormRegion. vb* .

2. Do třídy `TaskFormRegion` přidejte následující kód. Tento kód naplní pole se seznamem v oblasti formuláře pomocí řádku předmětu jednotlivých úkolů ze složky Úkoly Outlooku.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Do třídy `TaskFormRegion` přidejte následující kód. Tento kód provádí následující úlohy:

   - Vyhledá `Microsoft.Office.Interop.Outlook.TaskItem` ve složce úkoly voláním `FindTaskBySubjectName` pomocné metody a předáním předmětu požadované úlohy. `FindTaskBySubjectName`Pomocná metoda se přidá v dalším kroku.

   - Přidá `Microsoft.Office.Interop.Outlook.TaskItem.Subject` hodnoty a `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` do pole se seznamem závislých úkolů.

   - Přidá předmět úkolu do skrytého pole v oblasti formuláře. Skryté pole ukládá tyto hodnoty jako součást položky Outlooku.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Do třídy `TaskFormRegion` přidejte následující kód. Tento kód poskytuje pomocnou metodu `FindTaskBySubjectName` , která byla popsána v předchozím kroku.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Do třídy `TaskFormRegion` přidejte následující kód. Tento kód provádí následující úlohy:

   - Aktualizuje seznam v oblasti formuláře s aktuálním stavem dokončení jednotlivých závislých úloh.

   - Analyzuje skryté textové pole, aby získal předmět jednotlivých závislých úkolů. Pak vyhledá všechny `Microsoft.Office.Interop.Outlook.TaskItem` ve složce *úkoly* voláním `FindTaskBySubjectName` pomocné metody a předáním předmětu každé úlohy.

   - Přidá `Microsoft.Office.Interop.Outlook.TaskItem.Subject` hodnoty a `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` do pole se seznamem závislých úkolů.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. Proměnnou `TaskFormRegion_FormRegionShowing` obslužné rutiny události nahraďte následujícím kódem. Tento kód provádí následující úlohy:

   - Naplní pole se seznamem v oblasti formuláře pomocí předmětů úkolu, když se zobrazí oblast formuláře.

   - Vyvolá `RefreshTaskListBox` pomocnou metodu, když se zobrazí oblast formuláře. Tím se zobrazí všechny závislé úkoly, které byly přidány do seznamu, když byla položka dříve otevřena.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Testování oblasti formuláře aplikace Outlook
 Chcete-li otestovat oblast formuláře, přidejte úkoly do seznamu požadovaných úkolů v oblasti formuláře. Aktualizujte stav dokončení požadované úlohy a pak zobrazte aktualizovaný stav dokončení úkolu v seznamu požadovaných úloh.

### <a name="to-test-the-form-region"></a>Testování oblasti formuláře

1. Stisknutím klávesy **F5** spusťte projekt.

     Spustí se aplikace Outlook.

2. V Outlooku na kartě **Domů** klikněte na **nové položky** a pak klikněte na **úloha**.

3. Ve formuláři úlohy zadejte do pole **Předmět** **závislý úkol** .

4. Na kartě **úloha** na pásu karet ve skupině **Akce** klikněte na **Uložit & zavřít**.

5. V Outlooku na kartě **Domů** klikněte na **nové položky**, klikněte na **Další položky** a potom klikněte na **Zvolit formulář**.

6. V dialogovém okně **Zvolit formulář** klikněte na **TaskFormRegion** a pak klikněte na **otevřít**.

     Zobrazí se oblast formuláře **TaskFormRegion** . Tento formulář nahrazuje celý formulář úkolu. Pole se seznamem **Vybrat úlohu, která se mají přidat do seznamu závislé úlohy** , se naplní dalšími úkoly ve složce úkoly.

7. Ve formuláři úlohy zadejte do pole **Předmět** **primární úlohu**.

8. V poli **Vyberte úkol, který se má přidat do pole se seznamem závislých úloh** vyberte **závislý úkol** a pak klikněte na **přidat závislý úkol**.

     **0% dokončení – závislý úkol** v **této úloze závisí na následujícím poli se seznamem úkolů** . To ukazuje, že jste úspěšně zpracovali `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` Událost tlačítka.

9. Uložte a zavřete položku **primárního úkolu** .

10. Znovu otevřete položku závislé úlohy v aplikaci Outlook.

11. Ve formuláři závislé úlohy změňte pole **dokončeno%** na **50%**.

12. Na kartě **úloha** na pásu karet závislých úloh klikněte ve skupině **akce** na **Uložit & zavřít**.

13. Znovu otevřete položku **primárního úkolu** v aplikaci Outlook.

     **50% dokončení – závislý úkol** je nyní zobrazen v **tomto úkolu, závisí na následujícím** poli seznamu úkolů.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikace Outlook, najdete v těchto tématech:

- Další informace o návrhu vzhledu oblasti formuláře přetažením spravovaných ovládacích prvků do vizuálního návrháře naleznete v tématu [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Další informace o tom, jak přizpůsobit pás karet položky Outlooku, najdete v tématu [přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

- Další informace o tom, jak přidat vlastní podokno úloh do Outlooku, najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Viz také
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)

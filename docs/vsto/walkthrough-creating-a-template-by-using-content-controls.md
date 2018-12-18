---
title: 'Návod: Vytvoření šablony s použitím ovládacích prvků obsahu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e597f13d2627a8b3e40aa65926d1c990be839c38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833184"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Návod: Vytvoření šablony s použitím ovládacích prvků obsahu
  Tento návod ukazuje, jak vytvořit přizpůsobení úrovni dokumentu, který používá ovládací prvky obsahu k vytvoření obsahu strukturovaných a opakovaně použitelné šablony aplikace Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word vám umožní vytvořit kolekci částí opakovaně použitelné dokumentu s názvem *stavební bloky*. Tento návod ukazuje, jak vytvořit dvě tabulky jako stavební bloky. Každá tabulka obsahuje několik ovládacích prvků obsahu, které mohou obsahovat různé typy obsahu, jako je například ve formátu prostého textu nebo kalendářní data. Jednu z tabulek obsahuje informace o zaměstnance a dalších table obsahuje zpětné vazby od zákazníků.  
  
 Po vytvoření dokumentu z této šablony můžete přidat některou z tabulek v dokumentu s použitím několika <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objekty, které budou zobrazovat dostupná stavební bloky v šabloně.  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytváření tabulek, které obsahují obsah aplikace Word řídí šablony v době návrhu.  
  
- Ovládací prvek obsahu pole se seznamem a ovládací prvek obsahu rozevíracího seznamu naplnění prostřednictvím kódu programu.  
  
- Zabránění uživatelům v úpravách zadané tabulky.  
  
- Přidání tabulky do kolekce stavebního bloku šablony.  
  
- Vytvoření ovládacího prvku obsahu, která zobrazuje dostupné stavební bloky v šabloně.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Aplikace Microsoft Word.  
  
## <a name="create-a-new-word-template-project"></a>Vytvoření nového projektu šablony aplikace Word  
 Vytvořte šablonu aplikace Word tak, aby uživatelé snadno vytvořit vlastní kopie.  
  
### <a name="to-create-a-new-word-template-project"></a>Chcete-li vytvořit nový projekt šablony aplikace Word  
  
1.  Vytvoření projektu šablony aplikace Word s názvem **MyBuildingBlockTemplate**. V Průvodci vytvoříte nový textový dokument v řešení. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře se nová šablona aplikace Word v návrháři a přidá **MyBuildingBlockTemplate** projektu **Průzkumníka řešení**.  
  
## <a name="create-the-employee-table"></a>Vytvoření tabulky zaměstnanců  
 Vytvořte tabulku, která obsahuje čtyři různé typy ovládacích prvků obsahu kde může zadat informace o zaměstnance.  
  
### <a name="to-create-the-employee-table"></a>K vytvoření tabulky zaměstnanců  
  
1. V šabloně aplikace Word, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer na pásu karet, klepněte **vložit** kartu.  
  
2. V **tabulky** klikněte na možnost **tabulky**a vložit tabulku se dvěma sloupci a čtyři řádky.  
  
3. Zadejte text v prvním sloupci tak, aby se podobá následující sloupce:  
  
   ||  
   |-|  
   |**Jméno zaměstnance**|  
   |**Datum přijetí**|  
   |**Název**|  
   |**Obrázek**|  
  
4. Klikněte do první buňky ve druhém sloupci (vedle **jméno zaměstnance**).  
  
5. Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
   > [!NOTE]  
   >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. V **ovládací prvky** klikněte na položku **Text** tlačítko ![plaintextcontentcontrol –](../vsto/media/plaintextcontrol.gif "plaintextcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do první buňky.  
  
7. Klikněte na druhé buňce ve druhém sloupci (vedle **datum přijetí**).  
  
8. V **ovládací prvky** klikněte na položku **výběr data** tlačítko ![datepickercontentcontrol –](../vsto/media/datepicker.gif "datepickercontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do druhé buňce.  
  
9. Klikněte na třetí buňce v druhém sloupci (vedle **Title**).  
  
10. V **ovládací prvky** klikněte na položku **– pole se seznamem** tlačítko ![comboboxcontentcontrol –](../vsto/media/combobox.gif "comboboxcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>na třetí buňce.  
  
11. Klikněte na poslední buňku v druhém sloupci (vedle **obrázek**).  
  
12. V **ovládací prvky** klikněte na možnost **obsahu ovládacího prvku pro obrázek** tlačítko ![picturecontentcontrol –](../vsto/media/pictcontentcontrol.gif "picturecontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.PictureContentControl> do poslední buňky.  
  
## <a name="create-the-customer-feedback-table"></a>Vytvoření tabulky zpětné vazby zákazníka  
 Vytvořte tabulku, která obsahuje tři různé typy ovládacích prvků obsahu ve kterém může uživatel zadat informace o zákaznících zpětnou vazbu.  
  
### <a name="to-create-the-customer-feedback-table"></a>K vytvoření tabulky zpětné vazby zákazníka  
  
1. V šabloně aplikace Word, klepněte na řádek pod tabulkou Zaměstnanec, který jste přidali dříve a stiskněte klávesu **Enter** přidáte nový odstavec.  
  
2. Na pásu karet klikněte na tlačítko **vložit** kartu.  
  
3. V **tabulky** klikněte na možnost **tabulky**a vložit tabulku se dvěma sloupci a třemi řádky.  
  
4. Zadejte text v prvním sloupci tak, aby se podobá následující sloupce:  
  
   ||  
   |-|  
   |**Jméno zákazníka**|  
   |**Hodnocení spokojenosti**|  
   |**Komentáře**|  
  
5. Klikněte do první buňky druhý sloupec (vedle **jméno zákazníka**).  
  
6. Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
7. V **ovládací prvky** klikněte na položku **Text** tlačítko ![plaintextcontentcontrol –](../vsto/media/plaintextcontrol.gif "plaintextcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do první buňky.  
  
8. Klikněte na tlačítko v druhé buňce druhého sloupce (vedle **hodnocení spokojenosti**).  
  
9. V **ovládací prvky** klikněte na možnost **rozevíracího seznamu** tlačítko ![dropdownlistcontentcontrol –](../vsto/media/dropdownlist.gif "dropdownlistcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do druhé buňce.  
  
10. Klikněte do poslední buňky druhý sloupec (vedle **komentáře**).  
  
11. V **ovládací prvky** klikněte na položku **formátovaného textu** tlačítko ![richtextcontentcontrol –](../vsto/media/richtextcontrol.gif "richtextcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.RichTextContentControl>do poslední buňky.  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Naplnit pole se seznamem a rozevírací seznam prostřednictvím kódu programu  
 Ovládací prvky obsahu v době návrhu lze inicializovat pomocí **vlastnosti** okna v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Můžete je také inicializace za běhu, který vám umožní nastavit příslušné stavy počáteční dynamicky. V tomto návodu, použít k naplnění položek v kódu <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> za běhu, kde můžete zobrazit tyto objekty fungování.  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Úprava uživatelského rozhraní ovládacích prvků obsahu prostřednictvím kódu programu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument.cs** nebo **ThisDocument.vb**a potom klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující kód, který `ThisDocument` třídy. Tento kód deklaruje několik objektů, které použijete později v tomto názorném postupu.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy. Tento kód přidá položky <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> v tabulkách a sadách zástupný text, který se zobrazí v každém z těchto ovládacích prvků, než se uživatel upraví je.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>Zabránit uživatelům v úpravách tabulky zaměstnanců  
 Použití <xref:Microsoft.Office.Tools.Word.GroupContentControl> objekt jste deklarovali starší k ochraně tabulky zaměstnanců. Za ochranu v tabulce, uživatelé mohou stále upravovat ovládacích prvků obsahu v tabulce. Nelze však upravit text v prvním sloupci nebo upravujete v tabulce jinými způsoby, například přidávání nebo odstraňování řádků a sloupců. Další informace o tom, jak používat <xref:Microsoft.Office.Tools.Word.GroupContentControl> chránit část dokumentu, naleznete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>Chcete-li zabránit uživatelům v úpravách tabulky zaměstnanců  
  
1.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy za kód, který jste přidali v předchozím kroku. Tento kód zabraňuje uživatelům v úpravách vložením tabulky v tabulce zaměstnanců <xref:Microsoft.Office.Tools.Word.GroupContentControl> objekt, který jste dříve deklarovaný.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>Přidání tabulky do sběr stavebního bloku  
 Přidání tabulky do kolekce stavební bloky dokumentu v šabloně tak, aby uživatelé můžete vložit do dokumentu tabulky, které jste vytvořili. Další informace o stavební bloky dokumentu najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Přidání tabulky do stavební bloky v šabloně  
  
1.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy za kód, který jste přidali v předchozím kroku. Tento kód přidá nový stavební bloky, které obsahují tabulky, které Microsoft.Office.Interop.Word.BuildingBlockEntries kolekce, která obsahuje všechny opakovaně použitelné stavební bloky v šabloně. Nové stavební bloky jsou definovány v novou kategorii s názvem **zaměstnance a informace o zákaznících** a mají přiřazen typ stavebním blokem `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy za kód, který jste přidali v předchozím kroku. Tento kód odstraní tabulek ze šablony. Tabulky už nejsou potřebné, protože jste je přidali do Galerie opakovaně použitelných stavební bloky v šabloně. Dokument kód nejprve umístí do režimu návrhu, tak, aby chráněné zaměstnance tabulky je možné odstranit.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Vytvoření obsahu ovládacího prvku, který zobrazí stavební bloky  
 Vytvoření obsahu ovládacího prvku, který poskytuje přístup k stavební bloky (to znamená, že tabulky), které jste vytvořili dříve. Uživatelům můžete kliknout na tento ovládací prvek do tabulky přidat do dokumentu.  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Vytvoření obsahu ovládacího prvku, který zobrazí stavební bloky  
  
1.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy za kód, který jste přidali v předchozím kroku. Tento kód inicializuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objekt, který jste dříve deklarovaný. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Zobrazí všechny stavební bloky, které jsou definovány v kategorii **zaměstnance a informace o zákaznících** a které mají typ stavebním blokem `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>Testování projektu  
 Uživatelé mohou klepnutím ovládacími prvky galerie stavebních bloků v dokumentu, abychom Vložit tabulku zaměstnanců nebo zákazníků zpětnou vazbu. Uživatelé můžou zadejte nebo vyberte odpovědi v ovládacích prvcích obsahu v obou tabulkách. Uživatelé mohou upravovat jiné části tabulce zpětné vazby zákazníků, ale jsou správně neměl moct změnit jiné části tabulky zaměstnanců.  
  
### <a name="to-test-the-employee-table"></a>K otestování tabulky zaměstnanců  
  
1.  Stisknutím klávesy **F5** spusťte projekt.  
  
2.  Klikněte na tlačítko **zvolte první stavebním blokem** zobrazíte prvku první stavebním blokem galerie.  
  
3.  Klikněte na šipku rozevíracího seznamu vedle položky **vlastní galerie 1** záhlaví v ovládacím prvku a vyberte **tabulky zaměstnanců**.  
  
4.  Klikněte na tlačítko v buňce vpravo od **jméno zaměstnance** buňky a zadejte název.  
  
     Ověřte, že můžete přidat pouze text k této buňce nevrátí. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> Umožňuje uživatelům přidávat pouze text, ne jiné typy obsahu, jako jsou obrázky nebo tabulky.  
  
5.  Klikněte na tlačítko v buňce vpravo od **datum přijetí** buňku a vyberte datum v prvku Výběr data.  
  
6.  Klikněte na tlačítko v buňce vpravo od **název** buňku a vyberte jednu z úloh názvy v poli se seznamem.  
  
     Volitelně zadejte název pracovní pozice, který není v seznamu. To je možné, protože <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> umožňuje uživatelům vybrat ze seznamu položek nebo zadejte vlastní položky.  
  
7.  Klikněte na ikonu v buňce vpravo od **obrázek** buňky a přejděte na obrázek zobrazte je.  
  
8.  Znovu zkusíte přidat řádky nebo sloupce do tabulky a pokuste se odstranit řádky a sloupce z tabulky. Ověřte, že nelze upravovat v tabulce. <xref:Microsoft.Office.Tools.Word.GroupContentControl> Zabraňuje provedení změn.  
  
### <a name="to-test-the-customer-feedback-table"></a>K otestování tabulce zpětné vazby zákazníka  
  
1.  Klikněte na tlačítko **vyberte druhý stavebním blokem** zobrazíte druhý prvek obsahu galerie stavebních bloků.  
  
2.  Klikněte na šipku rozevíracího seznamu vedle položky **vlastní galerie 1** záhlaví v ovládacím prvku a vyberte **tabulky se zákazníky**.  
  
3.  Klikněte na tlačítko v buňce vpravo od **jméno zákazníka** buňky a zadejte název.  
  
4.  Klikněte na tlačítko v buňce vpravo od **hodnocení spokojenosti** buňku a vyberte jednu z dostupných možností.  
  
     Ověřte, že nelze zadat vlastní položku. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Umožňuje uživatelům pouze vybrat ze seznamu položek.  
  
5.  Klikněte na tlačítko v buňce vpravo od **komentáře** buňky a zadejte nějakými komentáři.  
  
     Volitelně můžete přidáte nějaký obsah než text, například obrázky nebo vložené tabulky. To je možné, protože <xref:Microsoft.Office.Tools.Word.RichTextContentControl> umožní uživatelům přidávat obsah než text.  
  
6.  Ověřte, že můžete přidat řádky nebo sloupce do tabulky a že můžete odstranit řádky a sloupce z tabulky. To je možné, protože nejsou chráněné v tabulce tak, že vložíte ho <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Zavřete šablonu.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak používat ovládací prvky obsahu z tohoto tématu:  
  
-   Vytvoření vazby ovládacích prvků obsahu na části kódu, také název vlastní části XML, které jsou vložené v dokumentu XML. Další informace najdete v tématu [návod: vytvoření vazby ovládacích prvků obsahu do vlastní části XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Ovládací prvky obsahu](../vsto/content-controls.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
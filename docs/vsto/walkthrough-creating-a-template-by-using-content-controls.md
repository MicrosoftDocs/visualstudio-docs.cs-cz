---
title: 'Návod: Vytvoření šablony s použitím ovládacích prvků obsahu'
description: Naučte se vytvářet přizpůsobení na úrovni dokumentu, které používá ovládací prvky obsahu k vytvoření strukturovaného a opakovaně použitelného obsahu v šabloně Microsoft Wordu.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7f78ca406d19461de7fa8e2a8c147b1003c9c852
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826964"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Návod: Vytvoření šablony s použitím ovládacích prvků obsahu
  Tento návod ukazuje, jak vytvořit přizpůsobení na úrovni dokumentu, které používá ovládací prvky obsahu k vytvoření strukturovaného a opakovaně použitelného obsahu v šabloně systém Microsoft Office Wordu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Aplikace Word umožňuje vytvořit kolekci opakovaně použitelných částí dokumentu s názvem *stavební bloky*. Tento návod ukazuje, jak vytvořit dvě tabulky jako stavební bloky. Každá tabulka obsahuje několik ovládacích prvků obsahu, které mohou obsahovat různé typy obsahu, například prostý text nebo kalendářní data. Jedna z tabulek obsahuje informace o zaměstnanci a druhá tabulka obsahuje zpětnou vazbu od zákazníků.

 Po vytvoření dokumentu ze šablony můžete do dokumentu přidat jednu z tabulek pomocí několika <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objektů, které zobrazí dostupné stavební bloky v šabloně.

 Tento návod znázorňuje následující úlohy:

- Vytváření tabulek, které obsahují ovládací prvky obsahu v šabloně aplikace Word v době návrhu.

- Naplnění ovládacího prvku obsahu pole se seznamem a ovládacího prvku rozevíracího seznamu pro programové řízení.

- Brání uživatelům v úpravách zadané tabulky.

- Přidání tabulek do kolekce stavebních bloků šablony.

- Vytvoření ovládacího prvku obsahu, který zobrazí dostupné stavební bloky v šabloně.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Vytvořit nový projekt šablony aplikace Word
 Vytvořte šablonu aplikace Word, aby uživatelé mohli snadno vytvářet vlastní kopie.

### <a name="to-create-a-new-word-template-project"></a>Vytvoření nového projektu šablony aplikace Word

1. Vytvořte projekt šablony aplikace Word s názvem **MyBuildingBlockTemplate**. V průvodci vytvořte nový dokument v řešení. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře novou šablonu aplikace Word v návrháři a přidá projekt **MyBuildingBlockTemplate** do **Průzkumník řešení**.

## <a name="create-the-employee-table"></a>Vytvoření tabulky Employee
 Vytvoří tabulku, která obsahuje čtyři různé typy ovládacích prvků obsahu, kde může uživatel zadat informace o zaměstnanci.

### <a name="to-create-the-employee-table"></a>Vytvoření tabulky Employee

1. V šabloně aplikace Word, která je hostována v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři, klikněte na pásu karet na kartu **Vložit** .

2. Ve skupině **tabulky** klikněte na **tabulka** a vložte tabulku se dvěma sloupci a čtyřmi řádky.

3. Zadejte text do prvního sloupce tak, aby vypadal jako následující sloupec:

   ||
   |-|
   |**Jméno zaměstnance**|
   |**Datum nástupu**|
   |**Název**|
   |**Obrázek**|

4. V druhém sloupci klikněte na první buňku (vedle **pole jméno zaměstnance**).

5. Na pásu karet klikněte na kartu **vývojář** .

   > [!NOTE]
   > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Ve skupině **ovládací prvky** kliknutím na tlačítko **text** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") přidejte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do první buňky.

7. Klikněte na druhou buňku ve druhém sloupci (vedle pole **Datum zařazení**).

8. Ve skupině **ovládací prvky** kliknutím na tlačítko pro **Výběr data** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") přidejte <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do druhé buňky.

9. Klikněte na třetí buňku ve druhém sloupci (vedle **nadpisu**).

10. Ve skupině **ovládací prvky** kliknutím na tlačítko **pole se seznamem** ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") přidejte <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> do třetí buňky.

11. Klikněte na poslední buňku ve druhém sloupci (vedle **obrázku**).

12. Ve skupině **ovládací prvky** kliknutím na tlačítko **ovládací prvek obrázek obsahu** ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") přidejte <xref:Microsoft.Office.Tools.Word.PictureContentControl> do poslední buňky.

## <a name="create-the-customer-feedback-table"></a>Vytvoření tabulky zpětné vazby od zákazníka
 Vytvořte tabulku, která obsahuje tři různé typy ovládacích prvků obsahu, kde může uživatel zadat informace o zpětné vazbě zákazníka.

### <a name="to-create-the-customer-feedback-table"></a>Vytvoření tabulky zpětné vazby od zákazníka

1. V šabloně aplikace Word klikněte na řádek za tabulkou zaměstnanců, kterou jste přidali dříve, a stisknutím klávesy **ENTER** přidejte nový odstavec.

2. Na pásu karet klikněte na kartu **Vložit** .

3. Ve skupině **tabulky** klikněte na **tabulka** a vložte tabulku se dvěma sloupci a třemi řádky.

4. Zadejte text do prvního sloupce tak, aby vypadal jako následující sloupec:

   ||
   |-|
   |**Jméno zákazníka**|
   |**Hodnocení spokojenosti**|
   |**Komentáře**|

5. Klikněte na první buňku druhého sloupce (vedle **pole název zákazníka**).

6. Na pásu karet klikněte na kartu **vývojář** .

7. Ve skupině **ovládací prvky** kliknutím na tlačítko **text** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") přidejte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do první buňky.

8. Klikněte na druhou buňku druhého sloupce (vedle **hodnocení spokojenost**).

9. Ve skupině **ovládací prvky** kliknutím na tlačítko **rozevíracího seznamu** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") přidejte <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do druhé buňky.

10. Klikněte na poslední buňku druhého sloupce (vedle **Komentáře**).

11. Ve skupině **ovládací prvky** kliknutím na tlačítko **s bohatým textem** ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") přidejte <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do poslední buňky.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Naplnění pole se seznamem a rozevíracího seznamu prostřednictvím kódu programu
 Ovládací prvky obsahu můžete inicializovat v době návrhu pomocí okna **vlastnosti** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Můžete je také inicializovat za běhu, což vám umožní dynamicky nastavit jejich počáteční stavy. Pro tento návod použijte kód k naplnění položek v <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> době běhu, abyste viděli, jak tyto objekty fungují.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Postup úpravy uživatelského rozhraní ovládacích prvků obsahu prostřednictvím kódu programu

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **ThisDocument. cs** nebo **ThisDocument. vb** a pak klikněte na **Zobrazit kód**.

2. Do třídy `ThisDocument` přidejte následující kód. Tento kód deklaruje několik objektů, které použijete později v tomto návodu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet1":::

3. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` . Tento kód přidá položky do <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> v tabulkách a nastaví zástupný text, který se zobrazí v každém z těchto ovládacích prvků předtím, než ho uživatel upraví.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet2":::

## <a name="prevent-users-from-editing-the-employee-table"></a>Zabránit uživatelům v úpravách tabulky zaměstnanců
 Použijte <xref:Microsoft.Office.Tools.Word.GroupContentControl> objekt, který jste předtím deklarovali k ochraně tabulky zaměstnanců. Po ochraně tabulky mohou uživatelé i nadále upravovat ovládací prvky obsahu v tabulce. Nemůžou ale upravovat text v prvním sloupci ani upravovat tabulku jinými způsoby, jako je přidání nebo odstranění řádků a sloupců. Další informace o tom, jak použít <xref:Microsoft.Office.Tools.Word.GroupContentControl> k ochraně části dokumentu, najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Zabránění uživatelům v úpravách tabulky Zaměstnanci

1. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` po kódu, který jste přidali v předchozím kroku. Tento kód zabrání uživatelům v úpravách tabulky Employees vložením tabulky do <xref:Microsoft.Office.Tools.Word.GroupContentControl> objektu, který jste předtím deklarovali.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet3":::

## <a name="add-the-tables-to-the-building-block-collection"></a>Přidání tabulek do kolekce stavebních bloků
 Přidejte tabulky do kolekce stavebních bloků dokumentů v šabloně, aby uživatelé mohli vkládat tabulky, které jste vytvořili do dokumentu. Další informace o stavebních blocích dokumentu naleznete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Přidání tabulek do stavebních bloků v šabloně

1. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` po kódu, který jste přidali v předchozím kroku. Tento kód přidá nové stavební bloky, které obsahují tabulky, do kolekce Microsoft. Office. Interop. Word. BuildingBlockEntries, která obsahuje všechny opakovaně použitelné stavební bloky v šabloně. Nové stavební bloky jsou definovány v nové kategorii s názvem **informace o zaměstnancích a zákaznících** a mají přiřazený typ stavebního bloku `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet4":::

2. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` po kódu, který jste přidali v předchozím kroku. Tento kód odstraní tabulky ze šablony. Tabulky již nejsou nutné, protože jste je přidali do galerie opakovaně použitelných stavebních bloků v šabloně. Kód nejprve vloží dokument do režimu návrhu, aby bylo možné odstranit chráněnou tabulku zaměstnanců.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet5":::

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Vytvoření ovládacího prvku obsahu, který zobrazuje stavební bloky
 Vytvořte ovládací prvek obsahu, který poskytuje přístup k stavebním blokům (tj. k tabulkám), které jste vytvořili dříve. Uživatelé mohou kliknutím na tento ovládací prvek přidat tabulky do dokumentu.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Vytvoření ovládacího prvku obsahu, který zobrazuje stavební bloky

1. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` po kódu, který jste přidali v předchozím kroku. Tento kód inicializuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objekt, který jste deklarovali dříve. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>Zobrazuje všechny stavební bloky, které jsou definovány v kategorii **zaměstnanci a informace o zákaznících** a které mají typ stavebního bloku `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-project"></a>Testování projektu
 Uživatelé můžou kliknout na ovládací prvky Galerie stavebních bloků v dokumentu a vložit tabulku zaměstnanců nebo tabulku zpětné vazby od zákazníka. Uživatelé mohou zadat nebo vybrat odpovědi v ovládacích prvcích obsahu v obou tabulkách. Uživatelé můžou upravovat ostatní části tabulky zpětné vazby od zákazníků, ale neměly by být schopné upravovat ostatní části tabulky zaměstnanců.

### <a name="to-test-the-employee-table"></a>Otestování tabulky Employee

1. Stisknutím klávesy **F5** spusťte projekt.

2. Klikněte na **zvolit první stavební blok** , abyste zobrazili první ovládací prvek obsahu Galerie stavebních bloků.

3. Klikněte na šipku rozevíracího seznamu vedle nadpisu **Vlastní galerie 1** v ovládacím prvku a vyberte **tabulka zaměstnanců**.

4. Klikněte na buňku napravo od buňky **název zaměstnance** a zadejte název.

     Ověřte, zda lze do této buňky přidat pouze text. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>Umožňuje uživatelům přidávat pouze text, nikoli jiné typy obsahu, jako je například umění nebo tabulka.

5. Klikněte na buňku napravo od buňky **Datum přijetí** a vyberte datum v ovládacím prvku pro výběr data.

6. Klikněte na buňku napravo od buňky **nadpisu** a vyberte jeden z titulů úlohy v poli se seznamem.

     Volitelně můžete zadat název funkce, která není v seznamu. To je možné, protože <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> umožňuje uživatelům vybrat ze seznamu položek nebo zadat vlastní položky.

7. Klikněte na ikonu v buňce napravo od buňky s **obrázkem** a přejděte na obrázek, který chcete zobrazit.

8. Pokuste se přidat řádky nebo sloupce do tabulky a pokusit se odstranit řádky a sloupce z tabulky. Ověřte, že tabulku nelze upravovat. Tím <xref:Microsoft.Office.Tools.Word.GroupContentControl> zabráníte v provádění jakýchkoli úprav.

### <a name="to-test-the-customer-feedback-table"></a>Testování tabulky zpětné vazby od zákazníka

1. Kliknutím na **zvolit druhý stavební blok** zobrazíte druhý ovládací prvek obsahu Galerie stavebních bloků.

2. Klikněte na šipku rozevíracího seznamu vedle nadpisu **Vlastní galerie 1** v ovládacím prvku a vyberte **tabulka zákazníků**.

3. Klikněte na buňku napravo od buňky **název zákazníka** a zadejte název.

4. Klikněte na buňku napravo od buňky **hodnocení spokojenost** a vyberte jednu z dostupných možností.

     Ověřte, že nemůžete zadat vlastní položku. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>Možnost umožňuje uživatelům vybrat pouze ze seznamu položek.

5. Klikněte na buňku napravo od buňky **Komentáře** a zadejte nějaké komentáře.

     Volitelně můžete přidat jiný obsah, než je text, jako je například obrázek nebo vložená tabulka. To je možné, protože <xref:Microsoft.Office.Tools.Word.RichTextContentControl> umožňuje uživatelům přidávat obsah jiný než text.

6. Ověřte, zda lze do tabulky přidat řádky nebo sloupce a zda lze z tabulky odstranit řádky a sloupce. To je možné, protože jste tabulku nechránili tak, že ji umístíte do <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

7. Zavřete šablonu.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak používat ovládací prvky obsahu, najdete v tomto tématu:

- Navažte ovládací prvky obsahu na části XML, které se také nazývají vlastní části XML, které jsou vloženy do dokumentu. Další informace najdete v tématu [Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>Viz také
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Ovládací prvky obsahu](../vsto/content-controls.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)

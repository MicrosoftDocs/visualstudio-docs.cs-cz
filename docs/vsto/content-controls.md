---
title: Ovládací prvky obsahu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 924f31ac38219453ae96fd573d968b18ce19c913
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672896"
---
# <a name="content-controls"></a>Ovládací prvky obsahu
  Ovládací prvky obsahu poskytují způsob, jak můžete na dokumentech návrhu a šablony, které mají tyto funkce:  
  
- Uživatelské rozhraní (UI), které má řízený vstup v podobě formuláře.  
  
- Omezení, které uživatelům zabránit v úprav chráněných oddílů dokumentu nebo šablony. Další informace najdete v tématu [ochrana částí dokumentů pomocí ovládacích prvků obsahu](#Protection).  
  
- Datové vazby ke zdroji dat Další informace najdete v tématu [vytvoření vazby dat na ovládací prvky obsahu](#DataBinding).  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [vytvoření vazby dat k aplikaci Word 2007 obsahu ovládacích prvků pomocí Visual Studio Tools pro systém Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>Přehled ovládacích prvků obsahu  
 Ovládací prvky obsahu obsahují uživatelské rozhraní, která je optimalizovaná pro oba uživatele vstupní a tisku. Pokud přidáte ovládací prvek obsahu k dokumentu, ovládací prvek je identifikován ohraničení, název a dočasný text, který může poskytnout pokyny pro uživatele. Ohraničení a záhlaví ovládacího prvku se nezobrazují v tištěné verze dokumentu.  
  
 Například pokud chcete, aby uživatel zadal datum v části dokumentu, můžete přidat ovládací prvek obsahu pro výběr data v dokumentu. Když uživatelé kliknou na ovládacím prvku Výběr data standardní uživatelské rozhraní se zobrazí. Můžete také nastavit vlastnosti ovládacího prvku, pokud chcete nastavit místní kalendář, který se zobrazí a zadat formát data. Po kliknutí na datum, uživatelského rozhraní ovládacího prvku je skrytá a pouze data se zobrazí, pokud uživatel vytiskne dokument.  
  
 Ovládací prvky obsahu také nápovědy, abyste udělali toto:  
  
- Zabraňte uživatelům v úpravách nebo odstraňování částí dokumentu. To je užitečné, pokud máte informace v dokumentu nebo šablony, která uživatelé by měli být schopni číst, ale nikoli upravovat, nebo pokud chcete, aby je uživatelé mohli upravit ovládací prvky obsahu, ale nikoli jejich odstraňování.  
  
- Svázat data částí dokumentu nebo šablony. Databázová pole, spravované objekty v lze svázat ovládací prvky obsahu [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], elementy XML, které jsou uloženy v dokumentu a jiných zdrojů dat.  
  
  V projektech na úrovni dokumentu můžete přidat ovládací prvky obsahu dokumentu v době návrhu nebo v době běhu. V doplňku VSTO projektů můžete přidat ovládací prvky obsahu do libovolného otevřeného dokumentu za běhu. Další informace najdete v tématu [postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Ovládací prvky obsahu můžete použít jenom v dokumentech, které jsou uložené ve formátu Open XML. Ovládací prvky obsahu nelze použít v dokumentech, které jsou uloženy v dokumentu Wordu 97 – 2003 (*doc*) formát.  
  
## <a name="types-of-content-controls"></a>Typy ovládacích prvků obsahu  
 Existují devět různé typy ovládacích prvků obsahu, které přidáte do dokumentů. Většina ovládací prvky obsahu mají odpovídající typ v <xref:Microsoft.Office.Tools.Word> oboru názvů. Můžete také použít obecný <xref:Microsoft.Office.Tools.Word.ContentControl>, což může představovat všechny dostupné ovládací prvky obsahu. Názorný postup ukazuje, jak využívat všechny dostupné ovládací prvky obsahu, najdete v části [návod: vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="build-block-gallery"></a>Sestavení bloku Galerie  
 Galerie stavebních bloků umožňuje uživatelům vybrat ze seznamu *stavební bloky dokumentu* vložit do dokumentu. Dokument stavební blok je část obsahu, který se vytvořil pro použití více než jednou, jako je například běžné titulní stránky, naformátovanou tabulku nebo hlavičku. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> typu. Další informace o stavebních bloků, naleznete v tématu [co je nového pro vývojáře v aplikaci Word 2007](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).  
  
### <a name="check-box"></a>Zaškrtávací políčko  
 Zaškrtávací políčko poskytuje uživatelské rozhraní, která představuje binární stav: zaškrtnuto nebo ne.  
  
 Na rozdíl od ostatních typů ovládacích prvků obsahu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] neposkytuje určitého typu, který představuje ovládací prvek zaškrtávací políčko obsahu. Jinými slovy, neexistuje žádný `CheckBoxContentControl` typu. Však můžete stále vytvořit ovládací prvek zaškrtávací políčko obsahu tak, že přidáte obecný <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentů prostřednictvím kódu programu. Další informace najdete v tématu [obsahu ovládací prvky zaškrtávacích políček v projektech aplikace Word](#checkbox).  
  
### <a name="combo-box"></a>Pole se seznamem  
 Pole se seznamem se zobrazí seznam položek, které můžou uživatelé vybrat. Na rozdíl od rozevíracího seznamu pole se seznamem umožní uživatelům přidávat své vlastní položky. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> typu.  
  
### <a name="date-picker"></a>Výběr data  
 Výběr data poskytuje kalendáře uživatelského rozhraní pro výběr data. V kalendáři se zobrazí, když koncový uživatel klepne na šipku rozevíracího seznamu v ovládacím prvku. Můžete použít místní kalendáře a jiné formáty. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> typu.  
  
### <a name="drop-down-list"></a>Rozevírací seznam  
 Rozevíracím seznamu zobrazí seznam položek, které můžou uživatelé vybrat. Na rozdíl od pole se seznamem rozevíracího seznamu, uživatelé nebudou moci pro přidání nebo úpravu položky. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> typu.  
  
### <a name="group"></a>Skupina  
 Ovládací prvek skupiny definuje oblast chráněný dokument, který uživatelé nedají upravit ani odstranit. Ovládací prvek skupiny může obsahovat všechny položky dokumentu, jako je například text, tabulek, grafiku a další ovládací prvky obsahu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.GroupContentControl> typu.  
  
### <a name="picture"></a>Obrázek  
 Ovládací prvek obrázek zobrazuje obrázek. Můžete určit bitovou kopii v době návrhu nebo běhu nebo uživatelům můžete kliknout na tento ovládací prvek a vyberte obrázek, který chcete vložit do dokumentu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.PictureContentControl> typu.  
  
### <a name="rich-text"></a>Formátovaný text  
 Ovládací prvek RTF obsahuje text nebo jiné položky, jako jsou tabulky, obrázky nebo jiné ovládací prvky obsahu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.RichTextContentControl> typu.  
  
### <a name="plain-text"></a>Prostý text  
 Textový ovládací prvek obsahuje text. Ovládací prvek jako prostý text nemůže obsahovat další položky, jako jsou tabulky, obrázky nebo jiné ovládací prvky obsahu. Kromě toho veškerý text ve formátu prostého textu ovládacího prvku má stejný formát. Pokud jste kurzívu o jedno slovo věty, která je ve formátu prostého textu ovládacího prvku, je třeba kurzívou veškerý text v ovládacím prvku. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> typu.  
  
### <a name="generic-content-control"></a>Obecný ovládací prvek obsahu  
 Je obecný ovládací prvek obsahu <xref:Microsoft.Office.Tools.Word.ContentControl> objekt, který může představovat jakýkoli z dostupných typů ovládacích prvků obsahu. Můžete změnit <xref:Microsoft.Office.Tools.Word.ContentControl> objekt chovají se jako jiný typ ovládacího prvku obsahu pomocí <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> vlastnost. Například, pokud vytvoříte <xref:Microsoft.Office.Tools.Word.ContentControl> objekt, představuje řídit prostého textu, můžete změnit ho v době běhu tak, aby se chová jako pole se seznamem.  
  
 Můžete vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objekty pouze v době běhu, není v době návrhu. Další informace najdete v tématu [postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>Společné funkce ovládacích prvků obsahu  
 Většina obsahu ovládací prvky se sdíleným sadu členů, které můžete použít k provádění běžných úloh. Následující tabulka popisuje některé úlohy, které můžete provést pomocí těchto členů.  
  
|Pro tuto úlohu:|postupujte takto:|  
|--------------------|--------------|  
|Získání nebo nastavení text, který se zobrazí v ovládacím prvku.|Použití **Text** vlastnost. **Poznámka:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> a <xref:Microsoft.Office.Tools.Word.ContentControl> typy nemají tuto vlastnost.|  
|Získání nebo nastavení dočasný text, který se zobrazí v ovládacím prvku, dokud uživatel neupraví ovládací prvek, ovládací prvek je naplněn daty ze zdroje dat nebo obsah ovládacího prvku se odstraní.|Použití **PlaceholderText** vlastnost. **Poznámka:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> typ nemá tuto vlastnost.|  
|Získání nebo nastavení název, který se zobrazí ohraničení ovládacího prvku obsahu, když na něj uživatel klikne.|Použití **název** vlastnost.|  
|Odeberte ovládací prvek z dokumentu automaticky po uživatel neupraví ovládací prvek. (Text v ovládacím prvku zůstane v dokumentu.)|Použití **dočasné** vlastnost.|  
|Kód spusťte, když uživatel klikne na ovládací prvek obsahu, nebo když se kurzor se přesune do ovládacího prvku obsahu prostřednictvím kódu programu.|Zpracování <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> události ovládacího prvku.|  
|Kód spusťte, když uživatel klikne na tlačítko mimo ovládací prvek obsahu, nebo když se přesune kurzor mimo ovládací prvek obsahu prostřednictvím kódu programu.|Zpracování <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> události ovládacího prvku.|  
|Spuštění kódu po obsahu ovládací prvek je přidán do dokumentu v důsledku znovu, nebo operaci vrátit zpět.|Zpracování <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> události ovládacího prvku.|  
|Spusťte kód bezprostředně před ovládací prvek obsahu se odstraní z dokumentu.|Zpracování <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> události ovládacího prvku.|  
  
##  <a name="Protection"></a> Ochrana částí dokumentů pomocí ovládacích prvků obsahu  
 Když chráníte část dokumentu, zabránit uživatelům v měnit nebo odstraňovat obsah v této části dokumentu. Existuje několik způsobů, jak můžete chránit částí dokumentů pomocí ovládacích prvků obsahu.  
  
 Pokud je oblast, kterou chcete chránit uvnitř ovládacího prvku obsahu, můžete zabránit uživatelům v úpravách nebo odstraňování ovládacího prvku vlastnosti ovládacího prvku obsahu:  
  
- **LockContents** vlastnost zabraňuje uživatelům v úpravách obsahu.  
  
- **LockContentControl** vlastnost zabraňuje uživatelům v odstranění ovládacího prvku.  
  
  Pokud v oblasti, které chcete chránit, není uvnitř ovládacího prvku obsahu, nebo pokud chcete chránit oblast, která obsahuje ovládací prvky obsahu a jiné typy obsahu, můžete vložit celé oblasti <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Na rozdíl od ostatních ovládacích prvků obsahu <xref:Microsoft.Office.Tools.Word.GroupContentControl> neposkytuje žádné uživatelské rozhraní, která je viditelná pro uživatele. Jejím jediným účelem je definování oblast, která uživatelé nelze upravit.  
  
> [!NOTE]  
>  Pokud jste vytvořili <xref:Microsoft.Office.Tools.Word.GroupContentControl> , která obsahuje vložené ovládací prvky obsahu, embedded ovládacích prvků obsahu nejsou chráněné automaticky. Je nutné použít **LockContents** vlastnosti každého vložit ovládací prvek zabránit uživatelům v úpravách jejich obsah.  
  
 Další informace o tom, jak Ochrana částí dokumentů pomocí ovládacích prvků obsahu najdete v tématu [postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> Vytvoření vazby dat na ovládací prvky obsahu  
 Pomocí vytvoření vazby ovládacího prvku obsahu ke zdroji dat můžou zobrazovat data v dokumentech. Při aktualizaci zdroje dat na ovládací prvek obsahu se změny projeví. Zpět do zdroje dat. můžete také uložit změny.  
  
 Ovládací prvky obsahu poskytují následující možnosti vazby dat:  
  
- Ovládací prvky obsahu můžete vázat na databázová pole nebo spravovaných objektů s použitím stejného modelu vazby dat jako Windows Forms.  
  
- Prvky v části XML lze svázat ovládací prvky obsahu (také s názvem *vlastní části XML*), který se vloží do dokumentu.  
  
  Přehled připojení k datům hostitelské ovládací prvky v řešeních pro systém Office, naleznete v tématu [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="use-the-windows-forms-data-binding-model"></a>Datový model vazby Windows Forms  
 Většina obsahu řídí podporu modelu jednoduché datové vazby, který používá Windows Forms. Jednoduchá vazba dat znamená, že je vytvořena vazba ovládacího prvku na jeden datový prvek, jako je například hodnota ve sloupci tabulky dat. Další informace najdete v tématu [a datové vazby Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 V projektech na úrovni dokumentu, lze svázat data ovládacích prvků obsahu s využitím **zdroje dat** okna v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace o tom, jak přidat ovládací prvky vázané na data obsahu do dokumentů najdete v tématu [postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md) a [postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 V následující tabulce jsou uvedeny ovládacích prvků obsahu, které můžete svázat s jednotlivými datovými typy v **zdroje dat** okna.  
  
|Datový typ|Výchozí ovládací prvek obsahu|Další ovládací prvky obsahu, které může být vázaný na tento typ dat|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Pole|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Žádné|  
  
 V úrovni dokumentu a projekty doplňku VSTO, můžete svázat ovládací prvek obsahu ke zdroji dat prostřednictvím kódu programu pomocí <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metodu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> vlastnost ovládacího prvku. Pokud to uděláte, předat řetězec **Text** k *propertyName* parametr <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody. **Text** je výchozí vlastnost vazby dat z ovládacích prvků obsahu.  
  
 Ovládací prvky obsahu také podporují obousměrné datové vazby, ve kterém se ke zdroji dat aktualizují změny v ovládacím prvku. Další informace najdete v tématu [postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  Ovládací prvky obsahu nepodporuje rozšířené datové vazby. Pokud svážete <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nebo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ke zdroji dat s využitím datového modelu Windows Forms, uživatelům se zobrazí jenom jedna hodnota po kliknutí ovládací prvek. Pokud chcete vytvořit vazbu tyto ovládací prvky na sadu hodnot dat, které uživatelé můžou vybírat, můžete tyto ovládací prvky vázat na prvky ve vlastní část XML.  
  
### <a name="bind-content-controls-to-custom-xml-parts"></a>Vytvoření vazby ovládacích prvků obsahu do vlastní části XML  
 Některé ovládací prvky obsahu můžete vázat na prvky ve vlastní části XML, které jsou vložené v dokumentu. Další informace o vlastních částí XML, naleznete v tématu [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md).  
  
 K vytvoření vazby ovládacího prvku obsahu na prvek v vlastní část XML, použijte **XMLMapping** vlastnost ovládacího prvku. Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> k `Price` element v rámci `Product` uzel ve vlastní část XML, který již byl přidán do dokumentu.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Návod, který ukazuje, jak svázat ovládací prvky obsahu vlastní části XML v další podrobnosti najdete v tématu [návod: vytvoření vazby ovládacích prvků obsahu do vlastní části XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Pokud vytvoříte vazbu ovládacího prvku obsahu na vlastní část XML, je automaticky povolen obousměrný datové vazby. Pokud uživatel upravuje text v ovládacím prvku, odpovídající elementy XML se automaticky aktualizují. Podobně pokud se změní hodnot prvků objektu vlastní části XML, ovládací prvky obsahu, které jsou vázány na prvky XML se zobrazí nová data.  
  
 Následující typy ovládacích prvků obsahu můžete vázat na vlastní části XML:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-bind-events-for-content-controls"></a>Vytvořit datovou vazbu s: události pro ovládací prvky obsahu  
 Všechny ovládací prvky obsahu poskytují sadu událostí, které můžou zpracovávat a provádět úlohy související s daty, jako je například ověření, že text v ovládacím prvku splňuje určitá kritéria, než se aktualizuje zdroj dat. Následující tabulka uvádí události ovládacího prvku obsahu, které se vztahují k vytváření datových vazeb.  
  
|Úloha|Událost|  
|----------|-----------|  
|Spuštění kódu těsně před plánovaným začátkem slovo automaticky aktualizuje text v ovládacím prvku obsahu, který je vázán na vlastní část XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Spuštění kódu těsně před plánovaným začátkem slovo automaticky aktualizuje data ve vlastní část XML, který je vázán na obsahu řízení (po změně textu v ovládacím prvku obsahu).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Spustíte vlastní kód pro ověření obsah ovládacího prvku podle vlastních kritérií.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Spuštění kódu po úspěšně ověřen obsah ovládacího prvku.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>Omezení ovládacích prvků obsahu  
 Při použití ovládacích prvků obsahu ve vašich projektech Office, mějte na paměti následující omezení.  
  
### <a name="behavior-differences-between-design-time-and-runtime"></a>Rozdíly v chování mezi i během návrhu a běhu  
 Mnoho omezení, které aplikace Microsoft Office Word ovládacích prvků obsahu ukládá v době běhu nejsou vynucená v době návrhu. Při návrhu řešení úrovni dokumentu v uživatelském rozhraní [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], je potřeba upravit ovládací prvky obsahu pouze způsobem, jsou podporovány v době běhu.  
  
 Při úpravě obsahu ovládacího prvku v době návrhu tak, aby ovládací prvek není podporován v době běhu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrhář nebude upozornění na nepodporované změny. Ale při ladění nebo spuštění projektu, nebo pokud uložíte a znovu otevřete projekt, Word se zobrazí na chybové zprávy a žádost o oprávnění k opravě dokumentu. Při opravě dokumentu aplikace Word odstraní všechny nepodporované obsahu a formátování v ovládacím prvku.  
  
 Například slovo nebrání můžete přidat tabulku pro <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> v době návrhu. Ale protože <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> objekty nesmí obsahovat tabulek v době běhu, Word se zobrazí chybová zpráva při otevření dokumentu.  
  
 Všimněte si také, že mnoho vlastností, které definují chování ovládacích prvků obsahu neprojeví v době návrhu. Například pokud nastavíte **LockContents** vlastnost obsahu ovládacího prvku na **True** v době návrhu, můžete upravit text v ovládacím prvku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře. Tato vlastnost pouze zabraňuje uživatelům v úpravách ovládacího prvku v době běhu.  
  
### <a name="event-limitations"></a>Omezení událostí  
 Ovládací prvky obsahu se neposkytuje událost, která se vyvolá, když uživatel změní text nebo jiné položky v ovládacím prvku. Například neexistuje žádná událost, která se vyvolá, když uživatel vybere jiné položce v <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nebo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Pokud chcete zjistit, když uživatel upraví obsah ovládacího prvku obsahu, můžete svázat ovládací prvek na vlastní část XML a následně zpracovat <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> událostí. Tato událost je aktivována, když uživatel změní obsah ovládacího prvku, který je vázán na vlastní část XML. Názorný postup ukazuje, jak vytvořit vazbu ovládacího prvku obsahu na vlastní část XML, naleznete v tématu [návod: vytvoření vazby ovládacích prvků obsahu do vlastní části XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Obsahu ovládací prvky zaškrtávacích políček v projektech aplikace Word  
 Word 2010 zavedl nový typ obsahu ovládacího prvku, který představuje zaškrtávací políčko. Ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] neposkytuje odpovídající typ CheckBoxContentControl pro použití v projektech pro systém Office. Vytvoření obsahu ovládacího prvku zaškrtávací políčko v [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo projektu aplikace Word 2010, použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> metodu pro vytvoření <xref:Microsoft.Office.Tools.Word.ContentControl> objektu a předejte <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> hodnota, která má metodu k určení obsahu ovládací prvek zaškrtávací políčko. Následující příklad kódu ukazuje, jak to provést.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Návod: Vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  

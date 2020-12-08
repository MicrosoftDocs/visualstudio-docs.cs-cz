---
title: Ovládací prvky obsahu
description: Seznamte se s ovládacími prvky obsahu a způsobem, jak ovládací prvky obsahu umožňují navrhovat dokumenty a šablony.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a34211c7fb1fa001719219b7d08baab65340bde5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848037"
---
# <a name="content-controls"></a>Ovládací prvky obsahu
  Ovládací prvky obsahu poskytují způsob návrhu dokumentů a šablon, které mají tyto funkce:

- Uživatelské rozhraní (UI), které má řízený vstup jako formulář.

- Omezení zabraňující uživatelům upravovat chráněné oddíly dokumentu nebo šablony. Další informace najdete v tématu [Ochrana částí dokumentů pomocí ovládacích prvků obsahu](#Protection).

- Datová vazba ke zdroji dat. Další informace najdete v tématu [vázání dat k ovládacím prvkům obsahu](#DataBinding).

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Související video ukázku naleznete v tématu [vázání dat na Word 2007 ovládací prvky obsahu pomocí Visual Studio Tools pro systém Office (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="overview-of-content-controls"></a>Přehled ovládacích prvků obsahu
 Ovládací prvky obsahu poskytují uživatelské rozhraní optimalizované pro vstup uživatele i pro tisk. Když přidáte ovládací prvek obsahu do dokumentu, ovládací prvek je identifikován ohraničením, nadpisem a dočasným textem, který může uživateli poskytnout pokyny. Ohraničení a název ovládacího prvku se nezobrazí v tištěných verzích dokumentu.

 Například pokud chcete, aby uživatel zadal datum v části dokumentu, můžete do dokumentu přidat ovládací prvek obsahu pro výběr data. Když uživatel klikne na ovládací prvek, zobrazí se standardní uživatelské rozhraní pro výběr data. Můžete také nastavit vlastnosti ovládacího prvku tak, aby se nastavil regionální kalendář, který se zobrazí, a zadání formátu data. Jakmile uživatel zvolí datum, uživatelské rozhraní ovládacího prvku bude skryto a zobrazí se pouze datum, pokud uživatel dokument vytiskne.

 Ovládací prvky obsahu vám také pomůžou provést následující akce:

- Znemožní uživatelům upravovat nebo odstraňovat části dokumentu. To je užitečné, pokud máte informace v dokumentu nebo šabloně, které by uživatelé měli mít oprávnění číst, ale nikoli upravovat, nebo pokud chcete, aby uživatelé mohli upravovat ovládací prvky obsahu, ale neodstraňují je.

- Vazba částí dokumentu nebo šablony na data. Ovládací prvky obsahu můžete navazovat na databázová pole, spravované objekty v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] prvcích XML, které jsou uloženy v dokumentu a dalších zdrojích dat.

  V projektech na úrovni dokumentu můžete do dokumentu přidat ovládací prvky obsahu v době návrhu nebo v době běhu. V projektech doplňku VSTO můžete přidat ovládací prvky obsahu do libovolného otevřeného dokumentu v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).

> [!NOTE]
> Ovládací prvky obsahu můžete použít pouze v dokumentech, které jsou uloženy ve formátu Open XML. Nemůžete použít ovládací prvky obsahu v dokumentech, které jsou uložené ve formátu dokumentu aplikace Word 97-2003 (*. doc*).

## <a name="types-of-content-controls"></a>Typy ovládacích prvků obsahu
 Existují devět různých typů ovládacích prvků obsahu, které lze přidat do dokumentů. Většina ovládacích prvků obsahu má odpovídající typ v <xref:Microsoft.Office.Tools.Word> oboru názvů. Můžete také použít obecné <xref:Microsoft.Office.Tools.Word.ContentControl> , které může představovat kterýkoli z dostupných ovládacích prvků obsahu. Návod, který ukazuje, jak použít jednotlivé dostupné ovládací prvky obsahu, naleznete v tématu [Návod: Vytvoření šablony pomocí ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

### <a name="build-block-gallery"></a>Galerie bloků sestavení
 Galerie stavebních bloků umožňuje uživatelům vybrat ze seznamu *stavebních bloků dokumentů* pro vložení do dokumentu. Stavební blok dokumentu je část obsahu, která byla vytvořena pro použití několikrát, jako je například společná titulní stránka, formátovaná tabulka nebo záhlaví. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> typ. Další informace o stavebních blocích najdete v tématu [co je nového pro vývojáře ve wordu 2007](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).

### <a name="check-box"></a>Zaškrtávací políčko
 Zaškrtávací políčko poskytuje uživatelské rozhraní, které představuje binární stav: vybráno nebo zrušeno.

 Na rozdíl od jiných typů ovládacích prvků obsahu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] neposkytuje konkrétní typ, který představuje ovládací prvek obsahu zaškrtávacího políčka. Jinými slovy, neexistuje žádný `CheckBoxContentControl` typ. Můžete však stále vytvořit ovládací prvek obsahu zaškrtávacího políčka přidáním obecného <xref:Microsoft.Office.Tools.Word.ContentControl> k dokumentu prostřednictvím kódu programu. Další informace najdete v tématu [ovládací prvky obsahu zaškrtávacího políčka v projektech aplikace Word](#checkbox).

### <a name="combo-box"></a>Pole se seznamem
 V poli se seznamem se zobrazí seznam položek, které mohou uživatelé vybrat. Na rozdíl od rozevíracího seznamu umožňuje pole se seznamem uživatelům přidat vlastní položky. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> typ.

### <a name="date-picker"></a>Výběr data
 Výběr data poskytuje uživatelské rozhraní kalendáře pro výběr data. Kalendář se zobrazí, když koncový uživatel klikne na šipku rozevíracího seznamu v ovládacím prvku. Můžete použít regionální kalendáře a jiné formáty data. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> typ.

### <a name="drop-down-list"></a>Rozevírací seznam
 V rozevíracím seznamu se zobrazí seznam položek, které mohou uživatelé vybrat. Na rozdíl od pole se seznamem neumožňuje uživatelům přidávat nebo upravovat položky. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> typ.

### <a name="group"></a>Skupina
 Ovládací prvek skupiny definuje chráněnou oblast dokumentu, kterou uživatelé nemohou upravovat ani odstraňovat. Ovládací prvek skupiny může obsahovat libovolné položky dokumentu, například text, tabulky, grafiku a další ovládací prvky obsahu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.GroupContentControl> typ.

### <a name="picture"></a>Obrázek
 Ovládací prvek obrázek zobrazí obrázek. Bitovou kopii můžete zadat v době návrhu nebo v době spuštění, nebo uživatelé můžou kliknout na tento ovládací prvek a vybrat obrázek, který chcete vložit do dokumentu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.PictureContentControl> typ.

### <a name="rich-text"></a>Bohatě vydaný text
 Ovládací prvek formátovaného textu obsahuje text nebo jiné položky, jako jsou tabulky, obrázky nebo jiné ovládací prvky obsahu. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.RichTextContentControl> typ.

### <a name="plain-text"></a>Prostý text
 Text obsahuje ovládací prvek prostého textu. Ovládací prvek prostého textu nemůže obsahovat další položky, jako jsou tabulky, obrázky nebo jiné ovládací prvky obsahu. Kromě toho má celý text v ovládacím prvku prostý text stejné formátování. Pokud například zobrazíte kurzívu jedno slovo věty, která je v ovládacím prvku prostý text, veškerý text v ovládacím prvku je kurzívou. Další informace najdete v tématu <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> typ.

### <a name="generic-content-control"></a>Obecný ovládací prvek obsahu
 Obecný ovládací prvek obsahu je <xref:Microsoft.Office.Tools.Word.ContentControl> objekt, který může představovat kterýkoli z dostupných typů ovládacích prvků obsahu. Objekt můžete změnit <xref:Microsoft.Office.Tools.Word.ContentControl> tak, aby se choval jako jiný typ ovládacího prvku obsahu pomocí <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> Vlastnosti. Například pokud vytvoříte <xref:Microsoft.Office.Tools.Word.ContentControl> objekt, který představuje ovládací prvek prostého textu, můžete jej změnit za běhu tak, aby se choval jako pole se seznamem.

 Objekty lze vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> pouze za běhu, nikoli v době návrhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).

## <a name="common-features-of-content-controls"></a>Běžné funkce ovládacích prvků obsahu
 Většina ovládacích prvků obsahu sdílí sadu členů, které můžete použít k provádění běžných úloh. Následující tabulka popisuje některé úlohy, které můžete provádět pomocí těchto členů.

|Pro tuto úlohu:|Postupujte takto:|
|--------------------|--------------|
|Získá nebo nastaví text, který se zobrazí v ovládacím prvku.|Použijte vlastnost **text** . **Poznámka:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typy a nemají <xref:Microsoft.Office.Tools.Word.ContentControl> tuto vlastnost.|
|Získá nebo nastaví dočasný text, který se zobrazí v ovládacím prvku, dokud uživatel neupraví ovládací prvek, ovládací prvek se naplní daty ze zdroje dat, nebo se odstraní obsah ovládacího prvku.|Použijte vlastnost **PlaceholderText** . **Poznámka:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typ nemá tuto vlastnost.|
|Získá nebo nastaví název, který se zobrazí v ohraničení ovládacího prvku obsahu, když na něj uživatel klikne.|Použijte vlastnost **title** .|
|Odebrat ovládací prvek z dokumentu automaticky poté, co uživatel upraví ovládací prvek. (Text v ovládacím prvku zůstane v dokumentu.)|Použijte **dočasnou** vlastnost.|
|Spustit kód, když uživatel klikne v ovládacím prvku obsahu, nebo když se kurzor přesune do ovládacího prvku obsahu programově.|Zpracujte <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> událost ovládacího prvku.|
|Spustí kód, když uživatel klikne mimo ovládací prvek obsahu, nebo když se kurzor přesune mimo ovládací prvek obsahu programově.|Zpracujte <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> událost ovládacího prvku.|
|Spustit kód po přidání ovládacího prvku obsahu do dokumentu v důsledku operace opakování nebo vrácení zpět.|Zpracujte <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> událost ovládacího prvku.|
|Spustit kód těsně před tím, než je ovládací prvek obsahu odstraněn z dokumentu.|Zpracujte <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> událost ovládacího prvku.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> Ochrana částí dokumentů pomocí ovládacích prvků obsahu
 Když chráníte část dokumentu, zabráníte uživatelům v této části dokumentu měnit ani odstraňovat obsah. Existuje několik způsobů, jak můžete chránit části dokumentu pomocí ovládacích prvků obsahu.

 Pokud je oblast, kterou chcete chránit, v ovládacím prvku obsahu, můžete použít vlastnosti ovládacího prvku obsahu a zabránit tak uživatelům v úpravách nebo odstraňování tohoto ovládacího prvku:

- Vlastnost **LockContents** zabraňuje uživatelům v úpravách obsahu.

- Vlastnost **LockContentControl** zabraňuje uživatelům v odstranění ovládacího prvku.

  Pokud oblast, kterou chcete chránit, není uvnitř ovládacího prvku obsahu, nebo pokud chcete chránit oblast obsahující ovládací prvky obsahu a další typy obsahu, můžete celou oblast umístit do <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Na rozdíl od jiných ovládacích prvků obsahu <xref:Microsoft.Office.Tools.Word.GroupContentControl> neposkytuje žádné uživatelské rozhraní, které je viditelné uživateli. Jeho jediným účelem je definovat oblast, kterou uživatelé nemohou upravovat.

> [!NOTE]
> Pokud vytvoříte objekt <xref:Microsoft.Office.Tools.Word.GroupContentControl> , který obsahuje ovládací prvky vloženého obsahu, ovládací prvky vloženého obsahu nejsou automaticky chráněny. Chcete-li uživatelům zabránit v úpravách jejich obsahu, je nutné použít vlastnost **LockContents** každého vloženého ovládacího prvku.

 Další informace o tom, jak používat ovládací prvky obsahu k ochraně částí dokumentů, naleznete v tématu [How to: Protect of Documents using a Content Controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> Svázání dat s ovládacími prvky obsahu
 Data můžete zobrazit v dokumentech pomocí vazby ovládacího prvku obsahu ke zdroji dat. Když je zdroj dat aktualizován, ovládací prvek obsahu tyto změny odráží. Změny můžete také uložit zpět do zdroje dat.

 Ovládací prvky obsahu poskytují následující možnosti datové vazby:

- Ovládací prvky obsahu můžete svázat s poli databáze nebo spravovanými objekty pomocí stejného modelu vázání dat jako model Windows Forms.

- Ovládací prvky obsahu můžete navazovat na prvky v částech XML (také s názvem *Custom XML Parts*), které jsou vložené v dokumentu.

  Přehled vazeb hostitelských ovládacích prvků v řešeních pro systém Office k datům najdete v tématu [vázání dat na ovládací prvky v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="use-the-windows-forms-data-binding-model"></a>Použití modelu model Windows Forms datové vazby
 Většina ovládacích prvků obsahu podporuje model jednoduché datové vazby, který model Windows Forms používá. Jednoduchá vazba dat znamená, že ovládací prvek je svázán s jedním datovým prvkem, jako je například hodnota ve sloupci tabulky dat. Další informace najdete v tématu [datové vazby a model Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 V projektech na úrovni dokumentu můžete vytvořit svázání dat s ovládacími prvky obsahu pomocí okna **zdroje dat** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace o tom, jak do dokumentů přidat ovládací prvky obsahu vázané na data, naleznete v tématu [How to: naplnit dokumenty daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md) a [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md).

 V následující tabulce jsou uvedeny ovládací prvky obsahu, které lze vytvořit s každým datovým typem v okně **zdroje dat** .

|Datový typ|Výchozí ovládací prvek obsahu|Další ovládací prvky obsahu, které mohou být vázány na tento datový typ|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> skupin|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Žádné|

 V projektech doplňku na úrovni dokumentu a VSTO můžete vytvořit propojení ovládacího prvku obsahu se zdrojem dat programově pomocí <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> vlastnosti ovládacího prvku. V takovém případě předejte **text** řetězce do parametru *PropertyName* <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody. Vlastnost **text** je výchozí vlastnost datové vazby ovládacích prvků obsahu.

 Ovládací prvky obsahu podporují také obousměrnou datovou vazbu, při které se změny v ovládacím prvku aktualizují na zdroj dat. Další informace najdete v tématu [Postup: aktualizace zdroje dat s daty z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

> [!NOTE]
> Ovládací prvky obsahu nepodporují složitou datovou vazbu. Pokud svážete <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nebo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ke zdroji dat pomocí model Windows Forms datového modelu, uživatelům se při kliknutí na ovládací prvek zobrazí pouze jedna hodnota. Chcete-li tyto ovládací prvky navážete na sadu hodnot dat, ze kterých si uživatelé mohou vybrat, můžete tyto ovládací prvky navazovat na prvky ve vlastní části XML.

### <a name="bind-content-controls-to-custom-xml-parts"></a>Svázání ovládacích prvků obsahu s vlastními částmi XML
 Můžete navazovat ovládací prvky obsahu pro prvky ve vlastních částech XML, které jsou vloženy do dokumentu. Další informace o vlastních částech XML naleznete v tématu [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).

 Chcete-li vytvořit propojení ovládacího prvku obsahu s prvkem ve vlastní části XML, použijte vlastnost **XmlMapping** ovládacího prvku. Následující příklad kódu ukazuje, jak vytvořit vazby <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> na `Price` prvek pod `Product` uzlem ve vlastní části XML, která již byla přidána do dokumentu.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 Návod, který ukazuje, jak navazovat ovládací prvky obsahu na vlastní části XML podrobněji, naleznete v tématu [Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

 Když svážete ovládací prvek obsahu s vlastní částkou XML, bude automaticky povoleno obousměrná datová vazba. Pokud uživatel upraví text v ovládacím prvku, odpovídající prvky XML jsou automaticky aktualizovány. Podobně, pokud dojde ke změně hodnot prvků ve vlastních částech XML, ovládací prvky obsahu, které jsou vázány na prvky XML, zobrazí nová data.

 Následující typy ovládacích prvků obsahu lze navazovat na vlastní části XML:

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>Události datové vazby pro ovládací prvky obsahu
 Všechny ovládací prvky obsahu poskytují sadu událostí, které lze zpracovat k provádění úloh souvisejících s daty, jako je například ověření, že text v ovládacím prvku splňuje určitá kritéria před aktualizací zdroje dat. V následující tabulce jsou uvedeny události řízení obsahu, které se vztahují k datové vazbě.

|Úloha|Událost|
|----------|-----------|
|Spustit kód těsně před tím, než aplikace Word automaticky aktualizuje text v ovládacím prvku obsahu, který je vázán na vlastní část XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Spustit kód těsně před tím, než aplikace Word automaticky aktualizuje data ve vlastní části XML, která je svázána s ovládacím prvkem obsahu (to znamená po změně textu v ovládacím prvku Content Control).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Spusťte vlastní kód pro ověření obsahu ovládacího prvku podle vlastních kritérií.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Spusťte kód po úspěšném ověření obsahu ovládacího prvku.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>Omezení ovládacích prvků obsahu
 Pokud používáte ovládací prvky obsahu v projektech Office, pamatujte na následující omezení.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Rozdíly v chování mezi časem návrhu a modulem runtime
 Mnohé z omezení, které systém Microsoft Office slovo ukládá v ovládacích prvcích obsahu v době běhu, nejsou v době návrhu vynucuje. Při návrhu uživatelského rozhraní řešení na úrovni dokumentu v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nezapomeňte upravit ovládací prvky obsahu pouze způsobem, který je podporován v době běhu.

 Pokud upravíte ovládací prvek obsahu v době návrhu způsobem, který ovládací prvek v době běhu nepodporuje, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrhář nebude upozorněn na nepodporované změny. Při ladění nebo spuštění projektu, nebo pokud uložíte a pak znovu otevřete projekt, aplikace Word zobrazí chybovou zprávu a požaduje oprávnění k opravě dokumentu. Při opravě dokumentu aplikace Word odebere veškerý Nepodporovaný obsah a formátování z ovládacího prvku.

 Například Word nebrání v přidávání tabulky <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> v době návrhu. Vzhledem k tomu, že <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> objekty nemůžou v době běhu obsahovat tabulky, Word při otevření dokumentu zobrazí chybovou zprávu.

 Všimněte si také, že mnoho vlastností definujících chování ovládacích prvků obsahu nemá žádný vliv v době návrhu. Například pokud nastavíte vlastnost **LockContents** ovládacího prvku obsahu na **hodnotu true** v době návrhu, můžete i nadále upravovat text v ovládacím prvku v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři. Tato vlastnost zabrání uživatelům v úpravách ovládacího prvku v době běhu.

### <a name="event-limitations"></a>Omezení událostí
 Ovládací prvky obsahu neposkytují událost, která je vyvolána, když uživatel změní text nebo jiné položky v ovládacím prvku. Například neexistuje žádná událost, která je vyvolána, když uživatel vybere jinou položku v <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nebo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> .

 Chcete-li určit, kdy uživatel upraví obsah ovládacího prvku obsahu, můžete navázáním ovládacího prvku na vlastní část XML a následně zpracovat <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> událost. Tato událost se vyvolá, když uživatel změní obsah ovládacího prvku vázaného na vlastní část XML. Návod, který ukazuje, jak vytvořit propojení ovládacího prvku obsahu s vlastní část XML, naleznete v tématu [Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Ovládací prvky obsahu zaškrtávacího políčka v projektech aplikace Word
 Word 2010 představil nový typ ovládacího prvku obsahu, který představuje zaškrtávací políčko. Ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] neposkytuje odpovídající typ CheckBoxContentControl, který můžete použít v projektech Office. Chcete-li vytvořit ovládací prvek obsahu zaškrtávacího políčka v [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projektu nebo ve wordu 2010, použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> metodu pro vytvoření <xref:Microsoft.Office.Tools.Word.ContentControl> objektu a předání <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> hodnoty metodě pro určení ovládacího prvku obsah zaškrtávacího políčka. Následující příklad kódu ukazuje, jak to provést.

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>Viz také
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Návod: Vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

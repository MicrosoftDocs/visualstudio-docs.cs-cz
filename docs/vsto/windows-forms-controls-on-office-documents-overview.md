---
title: Přehled model Windows Formsch ovládacích prvků v dokumentech Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a101f22bccb3624eccff1edcea502c9350991392
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254915"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Přehled model Windows Formsch ovládacích prvků v dokumentech Office
  Ovládací prvky model Windows Forms jsou objekty, se kterými můžou uživatelé interaktivně zadávat data nebo pracovat s nimi. V projektech na úrovni dokumentu pro systém Microsoft Office Excel a systém Microsoft Office Word můžete přidat model Windows Forms ovládací prvky do dokumentu nebo sešitu v projektu v době návrhu nebo můžete programově přidat tyto ovládací prvky v době běhu. Tyto ovládací prvky můžete programově přidat do libovolného otevřeného dokumentu nebo listu v době běhu v doplňku VSTO pro Excel nebo Word.

 Další informace najdete v tématu [jak: Přidejte model Windows Forms ovládací prvky do dokumentů](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)Office.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Použití model Windows Formsch ovládacích prvků

Do dokumentů můžete přidat ovládací prvky model Windows Forms a přizpůsobitelné prvky uživatelského rozhraní (UI), včetně podoken akcí, vlastních podoken úloh a model Windows Forms. Ovládací prvky model Windows Forms obvykle mají stejné chování jako na těchto jiných prvcích uživatelského rozhraní, ale některé rozdíly existují. Informace najdete v tématu [omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

Rozhodnutí, zda přidat model Windows Forms ovládací prvky do dokumentu nebo jiný prvek uživatelského rozhraní závisí na několika faktorech. Při návrhu uživatelského rozhraní řešení zvažte použití model Windows Formsch ovládacích prvků, jak je popsáno v následující tabulce.

V dokumentu.
- Když chcete zobrazit ovládací prvky 100% času.

- Pokud chcete, aby uživatelé zadali data přímo v dokumentu, například v dokumentech založených na formulářích, kde je plocha pro úpravy uzamčena.

- Když chcete, aby ovládací prvky zobrazovaly na řádku s daty v dokumentu. Například pokud přidáváte tlačítka na každý řádek objektu seznamu, budete chtít, aby byly v souladu s každou položkou seznamu.

V podokně akce nebo v vlastním podokně úloh.
- Pokud chcete uživateli poskytnout kontextové informace.

- Když chcete, aby se v dokumentu zobrazily jenom výsledky, a ne ovládací prvky dotazu a data.

- Chcete-li zajistit, že ovládací prvky nebudou vytištěny spolu s dokumentem.

- Pokud chcete zajistit, aby ovládací prvky nenarušily zobrazení dokumentu.

Ve formuláři Windows.
- Pokud chcete řídit velikost uživatelského rozhraní.

- Když chcete uživatelům zabránit v skrývání nebo odstraňování ovládacích prvků.

- Když chcete získat vstup od uživatele a zabránit tomu, aby uživatel v dokumentu prováděl cokoli, až do přijetí vstupu.

## <a name="add-windows-forms-controls-programmatically"></a>Přidání ovládacích prvků model Windows Forms programově
 Do dokumentů aplikace Word a sešitů aplikace Excel lze v době běhu přidat ovládací prvky model Windows Forms. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Poskytuje podpůrné metody pro přidání nejběžnějších model Windows Formsch ovládacích prvků. Tyto pomocné metody umožňují rychle přidat do dokumentu Office ovládací prvky a získat přístup k kombinovaným funkcím ovládacího prvku model Windows Forms a k funkcím, které se týkají sady Office, těchto ovládacích prvků.

 Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Použití ovládacích prvků model Windows Forms v projektech na úrovni dokumentu
 Některé aspekty použití model Windows Formsch ovládacích prvků v dokumentech jsou jedinečné v projektech na úrovni dokumentu, které umožňují návrh uživatelského rozhraní dokumentu pomocí návrháře sady Visual Studio.

### <a name="create-custom-user-controls"></a>Vytváření vlastních uživatelských ovládacích prvků
 Do projektu můžete přidat uživatelský ovládací prvek a pak ho přidat do **panelu nástrojů**. Uživatelský ovládací prvek pak můžete přetáhnout přímo do dokumentu stejným způsobem, jako byste do dokumentu přidali ovládací prvek model Windows Forms. Při vytváření uživatelských ovládacích prvků je potřeba mít na paměti několik věcí:

- Nevytvářejte **zapečetěný** uživatelský ovládací prvek. Když přetáhnete ovládací prvek do dokumentu, Visual Studio vygeneruje obálkovou třídu odvozenou z uživatelského ovládacího prvku pro její rozšiřování a podporu jejího použití v dokumentu. Pokud je uživatelský ovládací prvek **zapečetěný**, sada Visual Studio nemůže vygenerovat obálkovou třídu.

- Uživatelské ovládací prvky musí mít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **hodnotu true**. Uživatelské ovládací prvky vytvořené v rámci projektu Office mají tento atribut nastaven na **hodnotu true** ve výchozím nastavení, ale uživatelské ovládací prvky, které jsou součástí vnějších projektů, nemusí mít tento atribut nastaven na **hodnotu true**.

- Po přidání uživatelského ovládacího prvku do dokumentu neměňte název ani neodstraňujte <xref:System.Windows.Forms.UserControl> třídu z projektu. Pokud potřebujete změnit název uživatelského ovládacího prvku, musíte ho nejdřív odstranit z dokumentu a pak ho po změně názvu znovu přidat.

### <a name="arrange-controls-at-design-time"></a>Uspořádat ovládací prvky v době návrhu
 Pokud přidáte více ovládacích prvků do dokumentů aplikace Word a Excel v době návrhu, můžete rychle nastavit zarovnání všech vybraných ovládacích prvků pomocí panelů nástrojů **systém Microsoft Office Word** a **systém Microsoft Office Excel** v sadě Visual Studio. Tyto panely nástrojů jsou k dispozici pouze v případě, že je dokument nebo list otevřen v návrháři.

 Když v Návrháři vyberete více ovládacích prvků, můžete použít následující tlačítka na těchto panelech nástrojů k uspořádání ovládacích prvků:

- **Zarovnat doleva**

- **Zarovnat na střed**

- **Zarovnat práva**

- **Zarovnat nahoru**

- **Zarovnat doprostřed**

- **Zarovnat dolů**

- **Nastavit vodorovné mezery jako rovné**

- **Nastavit svislé mezery**

> [!NOTE]
> V projektech aplikace Word jsou tato tlačítka povolena pouze v případě, že vybrané ovládací prvky nejsou vloženy jako text. Ve výchozím nastavení jsou ovládací prvky, které přidáte do dokumentu v době návrhu, v souladu s textem.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Zabránit zobrazování starých dat v excelových sešitech během načítání
 Když přidáte model Windows Forms ovládací prvky do dokumentů nebo listů v době návrhu, ovládací prvky zůstanou v dokumentu, když ho uživatel zavře. Ovládací prvky přidané v době návrhu se označují také jako *statické ovládací prvky*.

 Při otevření sešitu aplikace Excel, který obsahuje statické ovládací prvky, sešit zobrazí rastrový obrázek ovládacího prvku v ovládacím prvku ActiveX, dokud kód přizpůsobení neběží a nenačte skutečný ovládací prvek. Aplikace Excel vytvoří tento rastrový obrázek a uloží ho do sešitu pokaždé, když je sešit uložený. Rastrový obrázek zobrazuje ovládací prvek tak, jak se zobrazil při posledním uložení sešitu, včetně všech dat, která ovládací prvek zobrazil. Další informace o ovládacím prvku ActiveX, který obsahuje model Windows Forms ovládací prvky a bitmapy, najdete v tématu [omezení model Windows Forms ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 V určitých podmínkách se kód nenačte a zobrazí se pouze rastrový obrázek, například když uživatel otevře sešit v režimu návrhu. Také pokud uživatel otevře sešit v počítači, který [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nemá nainstalován, nelze vlastní nastavení spustit, aby bylo možné načíst ovládací prvky, a proto je viditelná pouze rastrový obrázek ovládacího prvku. Před uložením sešitu a jeho odesláním jinému uživateli byste měli vždy odebrat osobní informace z ovládacích prvků v sešitech, abyste zajistili, že vaše osobní údaje nebudou omylem zveřejněny.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Přizpůsobit velikost ovládacího prvku na velikost buňky v excelovém listu
 Můžete nastavit, aby se při změně velikosti nadřazené buňky automaticky změnila velikost ovládacího prvku. Další informace najdete v tématu [jak: Změnit velikost ovládacích prvků v](../vsto/how-to-resize-controls-within-worksheet-cells.md)buňkách listu

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Přidat komponenty, které jsou sdíleny všemi listy
 Můžete přidat součásti, které chcete sdílet mezi všemi listy, například a <xref:System.Data.DataSet>, do návrháře sešitu místo do listů. Komponenta se zobrazí v zásobníku součásti.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Vzorec pro vkládání ovládacích prvků na excelový list
 Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

### <a name="layout-style-of-controls-on-a-word-document"></a>Styl rozložení ovládacích prvků v dokumentu aplikace Word
 Přidáte-li ovládací prvek do dokumentu aplikace Word v projektu na úrovni dokumentu pomocí návrháře aplikace Visual Studio, ovládací prvek je přidán v řádku s textem. Chcete-li změnit styl rozložení ovládacího prvku, klikněte pravým tlačítkem myši na ovládací prvek a potom klikněte na možnost **Formát ovládacího prvku**. Vyberte styl obtékání na stránce **rozložení** dialogového okna **Formát objektu** .

 Když přidáte ovládací prvek do dokumentu aplikace Word v době běhu, můžete určit styl rozložení nového ovládacího prvku `Add`pomocí jiné \< *třídy ovládacího prvku* <xref:Microsoft.Office.Tools.Word.ControlCollection> > přetížení třídy:

- Chcete-li přidat ovládací prvek na řádku s textem, použijte přetížení, které <xref:Microsoft.Office.Interop.Word.Range> přijímá a určuje umístění ovládacího prvku.

- Chcete-li přidat ovládací prvek jako plovoucí tvar, použijte přetížení, které přijímá levý a horní souřadnici ovládacího prvku.

  Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Pokud otevřete šablonu aplikace Word v návrháři aplikace Visual Studio, nevložené ovládací prvky v šabloně nemusí být viditelné, protože aplikace Visual Studio otevře šablonu v **normálním** zobrazení. Chcete-li zobrazit ovládací prvky, změňte zobrazení na **rozložení tisku**.

### <a name="controls-outside-the-main-document-body"></a>Ovládací prvky mimo tělo hlavního dokumentu
 Ovládací prvky model Windows Forms nejsou podporovány uvnitř záhlaví nebo zápatí, nebo v rámci vnořeného dokumentu.

### <a name="add-components-at-design-time"></a>Přidat komponenty v době návrhu
 Některé ovládací prvky nebo součásti nejsou v dokumentu viditelné a místo toho se zobrazují v zásobníku komponent. Visual Studio poskytuje zásobník komponent pro každé okno dokumentu. Přihrádka komponenty se zobrazí na obrazovce pouze v případě, že komponenty existují v dokumentu.

## <a name="see-also"></a>Viz také:
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Ovládací prvky model Windows Forms](/dotnet/framework/winforms/controls/index)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Postupy: Změnit velikost ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Postupy: Při tisku skrývat ovládací prvky na listech](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Návod: Změna formátování listů pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Návod: Změna formátování dokumentu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Návod: Zobrazení textu v textovém poli na listu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Návod: Zobrazení textu v textovém poli v dokumentu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Návod: Aktualizace grafu v dokumentu pomocí přepínačů](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Návod: Aktualizace grafu na listu pomocí přepínačů](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)

---
title: Ovládací prvky Windows Forms na dokumenty Office – přehled
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51c671a583e4e96b51ae6627de1fce738696fe22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892776"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Ovládací prvky Windows Forms na dokumenty Office – přehled
  Ovládací prvky Windows Forms jsou objekty, které mohou uživatelé komunikovat s a zadejte skript nebo manipulaci s daty. V projektech na úrovni dokumentu pro aplikaci Microsoft Office Excel a Microsoft Office Word můžete přidat ovládací prvky Windows Forms k dokumentu nebo sešitu ve vašem projektu v době návrhu nebo prostřednictvím kódu programu přidáte těchto ovládacích prvků za běhu. Tyto ovládací prvky můžete programově přidat otevřeného dokumentu nebo listu za běhu v doplňku VSTO pro Excel nebo Word.  
  
 Další informace najdete v tématu [postupy: Přidání formuláře Windows ovládacích prvků do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Použití ovládacích prvků Windows Forms  
 Můžete přidat ovládací prvky Windows Forms k dokumentům a prvky přizpůsobitelné uživatelského rozhraní (UI), včetně podokna akcí, vlastní podokna úloh a Windows Forms. Ovládací prvky Windows Forms v dokumentech jako na tyto další prvky uživatelského rozhraní obvykle mají stejné chování, ale existuje několik rozdílů. Informace najdete v tématu [omezení Windows Forms ovládací prvky v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Rozhodnutí, jestli se má přidat do dokumentu nebo jiný prvek uživatelského rozhraní ovládacích prvků Windows Forms závisí na několika faktorech. Při navrhování uživatelského rozhraní vašeho řešení, zvažte použití ovládacích prvků Windows Forms, jak je popsáno v následující tabulce.  
  
 V dokumentu.  
 -   Pokud chcete zobrazit ovládací prvky 100 % času.  
  
- Pokud chcete, aby uživatelé pro zadávání dat přímo v dokumentu, například v založené na formulářích dokumenty, kde je uzamčen na úpravy plochu.  
  
- Když chcete ovládacích prvků pro zobrazení tato data v dokumentu. Například při přidávání tlačítek do jednotlivých řádků seznamu objektů, je by představám souladu s každou položku seznamu.  
  
  V podokně Akce nebo vlastního podokna úloh.  
  -   Pokud chcete poskytovat kontextové informace pro uživatele.  
  
- Když chcete pouze výsledky se zobrazí v dokumentu a ne ovládací prvky dotazu a data.  
  
- Pokud chcete zajistit, že nejsou zobrazeny ovládací prvky s dokumentem.  
  
- Pokud chcete zajistit, že ovládací prvky nejsou v konfliktu za dokumentu.  
  
  Ve formuláři Windows.  
  -   Pokud chcete určit velikost uživatelského rozhraní.  
  
- Pokud chcete zabránit uživatelům ve skryjete nebo odstranění ovládacích prvků.  
  
- Pokud chcete získat vstupy od uživatele a zabrání uživateli v teď zrovna nic nedělá v dokumentu, dokud přijetí vstupu.  
  
## <a name="add-windows-forms-controls-programmatically"></a>Přidání ovládacích prvků Windows Forms prostřednictvím kódu programu  
 Můžete přidat ovládací prvky Windows Forms do dokumentů aplikace Word a sešitů aplikace Excel v době běhu. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Poskytuje pomocné metody pro přidání většiny běžných ovládacích prvků Windows Forms. Tyto pomocné metody vám umožňují rychle přidat ovládacích prvků do dokumentů Office a přístup funkčnost ovládacího prvku Windows Forms a funkcím souvisejícím s Office těchto ovládacích prvků.  
  
 Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>Použití ovládacích prvků Windows Forms v projekty na úrovni dokumentu  
 Některé aspekty pomocí ovládacích prvků Windows Forms v dokumentech jsou jedinečné pro projekty na úrovni dokumentu, které vám umožní navrhnout dokumentu uživatelského rozhraní pomocí návrháře aplikace Visual Studio.  
  
### <a name="create-custom-user-controls"></a>Vytvoření vlastních uživatelských ovládacích prvků  
 Můžete přidat uživatelský ovládací prvek do projektu a pak ho přidat do **nástrojů**. Potom můžete přetáhnout uživatelského ovládacího prvku přímo do dokumentu stejným způsobem můžete přidat ovládacího prvku Windows Forms do dokumentu. Existují některé co je potřeba vzít v úvahu při vytváření uživatelských ovládacích prvků:  
  
-   Nevytvářejte **zapečetěné** uživatelského ovládacího prvku. Při přetažení ovládacího prvku do dokumentu sady Visual Studio generuje obálkovou třídu odvozenou z ovládacího prvku uživatel ji rozšířit a podporovat jejich použití v dokumentu. Pokud uživatelský ovládací prvek **zapečetěné**, Visual Studio nelze generovat obálkovou třídu.  
  
-   Uživatelské ovládací prvky musí mít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **true**. Uživatelské ovládací prvky vytvořené v projektu aplikace Office mají tento atribut nastavený na **true** ve výchozím nastavení, ale uživatelské ovládací prvky, které jsou součástí mimo projekty nemusí mít tento atribut nastavený na **true**.  
  
-   Po přidání uživatelského ovládacího prvku dokument nelze přejmenovat nebo odstranit <xref:System.Windows.Forms.UserControl> třídy z projektu. Pokud potřebujete změnit název uživatelského ovládacího prvku musíte nejprve odstranit z dokumentu a pak ho znovu přidat po změně názvu.  
  
### <a name="arrange-controls-at-design-time"></a>Uspořádání ovládacích prvků v době návrhu  
 Pokud přidáte více ovládacích prvků do dokumentů aplikace Word a Excel v době návrhu, můžete rychle nastavit zarovnání všech vybraných ovládacích prvků pomocí **Microsoft Office Word** a **aplikace Microsoft Office Excel**panelů nástrojů v sadě Visual Studio. Panely nástrojů jsou k dispozici pouze v případě, že je otevřen v Návrháři dokumentu nebo sešitu.  
  
 Když vyberete více ovládacích prvků v návrháři, vám pomůže následující tlačítka na panely nástrojů uspořádat ovládací prvky:  
  
-   **Zarovnat doleva**  
  
-   **Zarovnat centra**  
  
-   **Zarovnat doprava**  
  
-   **Zarovnat nahoru**  
  
-   **Zarovnat středy**  
  
-   **Zarovnat dolů**  
  
-   **Stejné vodorovné mezery**  
  
-   **Stejné svislé mezery**  
  
> [!NOTE]  
>  V projektech aplikace Word tato tlačítka jsou povolena pouze v případě, že nejsou vybrané ovládací prvky v textu. Ve výchozím nastavení jsou ovládací prvky, které přidáte do dokumentu v době návrhu v textu.  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Zabránit zobrazování v sešitech aplikace Excel během načítání stará data  
 Když přidáte ovládací prvky Windows Forms do dokumentů nebo listů v době návrhu, zůstávají ovládací prvky v dokumentu, při zavření dokumentu. Ovládacích prvků přidaných v době návrhu se také označují jako *statické ovládací prvky*.  
  
 Po otevření Excelového sešitu, který obsahuje statické ovládací prvky sešitu dokud přizpůsobení kód spustí a načte skutečný ovládací prvek zobrazuje rastrový obrázek ovládacího prvku v ovládacím prvku ActiveX. Excel vytvoří tento rastrový obrázek a uloží jej v sešitu pokaždé, když sešit uložený. Rastrový obrázek ukazuje ovládací prvek, jak se při posledním uložení sešitu, včetně všechna data, která byla zobrazení ovládacího prvku. Další informace o ovládacím prvku ActiveX, který obsahuje ovládací prvky Windows Forms a rastrové obrázky, naleznete v tématu [omezení Windows Forms ovládací prvky v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Za určitých podmínek zatížení kód a zobrazí pouze rastrový obrázek, například když uživatel otevře sešit v režimu návrhu. Také pokud uživatel otevře sešit v počítači, který nemá [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalovaná, nelze spustit přizpůsobení načíst ovládací prvky a proto je viditelná pouze rastrový obrázek ovládacího prvku. Vždy byste měli odebrat osobní údaje z ovládacích prvků v sešitech před uložením sešitu a odesílá je do jiného uživatele k zajištění, že se omylem zveřejněn vaše osobní údaje.  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Velikost ovládacího prvku na velikost buňky v listu aplikace Excel  
 Můžete nastavit ovládací prvek změnit velikost automaticky při změně velikosti nadřazené buňky. Další informace najdete v tématu [postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Přidat součásti, které jsou sdíleny ve všech listů  
 Můžete přidat komponenty, které chcete sdílet mezi všechny listy, například <xref:System.Data.DataSet>, do návrháře sešitu místo do listů. Součást se zobrazí v panelu komponent.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Vzorec pro vkládání ovládacích prvků na list aplikace Excel  
 Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Styl rozložení ovládacích prvků na dokumentu aplikace Word  
 Při přidání ovládacího prvku do dokumentu aplikace Word v projektu úrovni dokumentu pomocí návrháře aplikace Visual Studio je ovládací prvek přidán v textu. Chcete-li změnit styl rozložení ovládacího prvku, klikněte pravým tlačítkem na ovládací prvek a potom klikněte na **formát ovládacího prvku**. Vyberte styl zabalení na **rozložení** stránku **formát objektu** dialogové okno.  
  
 Při přidání ovládacího prvku do dokumentu aplikace Word v době běhu, můžete zadat požadovaný styl rozložení nového ovládacího prvku s použitím různých `Add` \< *třídu ovládacího prvku*> přetížení metody <xref:Microsoft.Office.Tools.Word.ControlCollection> třídy:  
  
- Přidání ovládacího prvku v textu, použijte přetížení, která přijímá <xref:Microsoft.Office.Interop.Word.Range> , která určuje umístění ovládacího prvku.  
  
- Přidání ovládacího prvku jako obrazec s plovoucí desetinnou čárkou, použijte přetížení, která přijímá souřadnice levého a horního ovládacího prvku.  
  
  Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Pokud otevřete šablonu aplikace Word v návrháři aplikace Visual Studio, protože Visual Studio otevře šablonu v nemusí zobrazovat nevložená ovládací prvky na této šabloně **normální** zobrazení. Chcete-li zobrazit ovládací prvky, změňte zobrazení tak, aby **rozložení při tisku**.  
  
### <a name="controls-outside-the-main-document-body"></a>Ovládací prvky mimo tělo hlavního dokumentu  
 Ovládací prvky Windows Forms nejsou podporovány v záhlaví nebo zápatí stránky, nebo v rámci vnořeného dokumentu.  
  
### <a name="add-components-at-design-time"></a>Přidat součásti v době návrhu  
 Některé ovládací prvky nebo součásti nejsou viditelné v dokumentu a místo toho se zobrazí v podokně komponent. Visual Studio poskytuje hlavní panel komponenty pro každé okno dokumentu. Panelu komponent se zobrazí na obrazovce pouze v případě, že součásti existovat v dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Ovládací prvky Windows Forms](/dotnet/framework/winforms/controls/index)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Postupy: skrytí ovládacích prvků na listech při tisku](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Návod: Změna formátování listů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Návod: Změna formátování dokumentů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Návod: Zobrazení textu v textovém poli na listu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Návod: Zobrazení textu v textovém poli v dokumentu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Návod: Aktualizace grafu v dokumentu s použitím přepínačů](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Návod: Aktualizace grafu na listu s použitím přepínačů](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  
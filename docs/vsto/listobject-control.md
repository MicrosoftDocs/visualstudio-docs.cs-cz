---
title: ListObject – ovládací prvek
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fe8191acc2bab7fbcfa2f21ef203f6057535a75
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676029"
---
# <a name="listobject-control"></a>ListObject – ovládací prvek
  <xref:Microsoft.Office.Tools.Excel.ListObject> Je ovládací prvek seznamu, který zpřístupňuje události a může být vázaný na data. Když přidáte seznam do listu, vytvoří Visual Studio <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který můžete programovat proti přímo bez nutnosti procházení objektový model aplikace Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Vytvoření ovládacího prvku  
 Projekty na úrovni dokumentu, můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků na list v době návrhu nebo v době běhu. Projekty doplňků VSTO, můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků na listech pouze za běhu. Další informace najdete v tématu [postupy: Přidání ListObject – ovládací prvky do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Ve výchozím nastavení, nejsou trvalé dynamicky vytvořený seznam objektů v listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="bind-data-to-the-control"></a>Vytvoření vazby dat k ovládacímu prvku  
 A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek podporuje jednoduché a komplexní datovou vazbu. <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek může být vázán na zdroji dat pomocí <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> a <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> vlastnosti v době návrhu nebo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metoda za běhu.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.ListObject> Automaticky aktualizuje, když je vázán na zdroj dat, jako například <xref:System.Data.DataTable>, která vyvolává události, když se data změní. Svážete-li <xref:Microsoft.Office.Tools.Excel.ListObject> ke zdroji dat, který nevyvolá události, když se data změní, musíte zavolat <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> nebo <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> způsob aktualizace <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Když přidáte <xref:Microsoft.Office.Tools.Excel.ListObject> na listu buňku mapováním opakující se element schématu na tuto buňku, Visual Studio automaticky mapuje <xref:Microsoft.Office.Tools.Excel.ListObject> pro generované datová sada. Ale <xref:Microsoft.Office.Tools.Excel.ListObject> není automaticky vázán na data. Můžete provést kroky k vytvoření vazby <xref:Microsoft.Office.Tools.Excel.ListObject> do datové sady v době návrhu nebo za běhu v projektu úrovni dokumentu. Můžete programově vytvořit vazbu <xref:Microsoft.Office.Tools.Excel.ListObject> k datové sadě za běhu v doplňku VSTO.  
  
 Protože data jsou oddělená od <xref:Microsoft.Office.Tools.Excel.ListObject>, by měla přidávat a odebírat data prostřednictvím vázané datové sady a ne přímo prostřednictvím <xref:Microsoft.Office.Tools.Excel.ListObject>. Pokud prostřednictvím každý použitý mechanizmus, se aktualizuje data v datové sadě vázané <xref:Microsoft.Office.Tools.Excel.ListObject> změny automaticky odrazí v ovládacím prvku. Další informace najdete v tématu [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Můžete rychle přejít k vyplnění <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku pomocí vytvoření vazby <xref:Microsoft.Office.Tools.Excel.ListObject> ke zdroji dat. Pokud upravíte data v vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject>, změny se automaticky provedeny ve zdroji dat. Pokud chcete, aby vyplnil <xref:Microsoft.Office.Tools.Excel.ListObject> a potom povolit uživatelům změnit data v <xref:Microsoft.Office.Tools.Excel.ListObject> beze změny zdroje dat, můžete použít <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metodu detach <xref:Microsoft.Office.Tools.Excel.ListObject> ze zdroje dat. Další informace najdete v tématu [postupy: vyplnění ListObject – ovládací prvky s daty](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  Vytváření datových vazeb není podporováno na překrývající se <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků.  
  
### <a name="improve-performance-in-listobject-controls"></a>Zlepšení výkonu ovládacích prvků ListObject  
 Čtení souboru XML do vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek je spíše pomalejší, pokud nejprve vazbu ovládacího prvku a následně zavolat <xref:System.Data.DataSet.ReadXml%2A> pro naplnění dataset. Chcete-li zvýšit výkon, zavolejte <xref:System.Data.DataSet.ReadXml%2A> před vazbu ovládacího prvku.  
  
### <a name="disconnect-listobject-controls-from-the-data-source"></a>Odpojit ovládacích prvků ListObject ze zdroje dat.  
 Po vyplnění <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku s daty pomocí vazby ke zdroji dat, můžete odpojit ho tak, aby se změny provedené v datech v objektu seznamu nemají vliv na zdroj dat. Další informace najdete v tématu [postupy: vyplnění ListObject – ovládací prvky s daty](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### <a name="restore-column-and-row-order"></a>Obnovení pořadí sloupců a řádků  
 Po vytvoření vazby dat k <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který byl přidán do dokumentu v době návrhu, Visual Studio uchovává informace o pořadí sloupců a řádků pokaždé, když sešit uložený. Pokud se uživatel přesune <xref:Microsoft.Office.Tools.Excel.ListObject> sloupců nebo řádků za běhu, při příštím otevření sešitu zachování nové pořadí a <xref:Microsoft.Office.Tools.Excel.ListObject> ke zdroji dat znovu naváže ovládací prvek.  
  
 Pokud chcete provést obnovení <xref:Microsoft.Office.Tools.Excel.ListObject> na jeho původní pořadí sloupců a řádků, můžete volat <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> metody. Tato metoda odstraní vlastní šablony dokumentů vlastnosti související s sloupec a zadaný řádek pořadí <xref:Microsoft.Office.Tools.Excel.ListObject>. Volejte tuto metodu z <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> událostí v sešitu, pokud nechcete zachovat pořadí sloupců a řádků <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## <a name="format"></a>Formát  
 Který lze použít k formátování <xref:Microsoft.Office.Interop.Excel.ListObject> lze použít u <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku. To zahrnuje ohraničení, písma, formát čísla a styly. Koncoví uživatelé mohou změnit uspořádání sloupců v vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject>, a tyto změny se zachovat pomocí poskytnutého dokumentu <xref:Microsoft.Office.Tools.Excel.ListObject> byl přidán do dokumentu v době návrhu. Při příštím otevření dokumentu, objekt seznamu bude vázán ke stejnému zdroji dat, ale pořadí sloupců se změny uživatelů projeví.  
  
## <a name="add-and-remove-columns-at-runtime"></a>Přidat a odebrat sloupce za běhu  
 Nemůžete ručně přidat nebo odebrat sloupce v vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku za běhu. Pokud koncový uživatel pokusí odstranit sloupec, se okamžitě obnoví a všechny sloupce, které přidává se odeberou. Proto je potřeba napsat kód, který vysvětlovat uživatelům, proč jim nelze provádět tyto akce na <xref:Microsoft.Office.Tools.Excel.ListObject> , který je vázán na data. Visual Studio obsahuje několik událostí <xref:Microsoft.Office.Tools.Excel.ListObject> související s datovou vazbu. Například můžete použít <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> události a upozornit uživatele, kteří se pokusí odstranit data nejde odstranit a byla obnovena.  
  
## <a name="add-and-remove-rows-at-runtime"></a>Přidání a odebrání řádků za běhu  
 Můžete ručně přidat a odebrat řádky v vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, pokud zdroj dat umožňuje přidání nových řádků a není jen pro čtení. Můžete napsat kód před událostmi, jako <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> ověřit data. Další informace najdete v tématu [postupy: ověření dat při přidání nového řádku do ovládacího prvku ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Vztah mezi objektem seznamu do zdroje dat. někdy způsobí běžné chyby. Například můžete namapovat sloupce, které chcete zobrazit v <xref:Microsoft.Office.Tools.Excel.ListObject>, takže pokud vynecháte sloupce, které mají omezení, jako je například pole, ve kterém nelze přijmout hodnoty null, chyby jsou vyvolány při každém vytvoření řádku. Můžete napsat kód v obslužné rutině události pro přidání chybějících hodnot <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> událostí.  
  
## <a name="rename-listobject-controls-in-excel"></a>Přejmenování ovládacích prvků ListObject v aplikaci Excel  
 Excel umožňuje uživatelům změnit název tabulky aplikace Excel v době běhu pomocí **návrhu** kartu. Ale <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek nepodporuje tuto funkci. Pokud se uživatel pokusí o přejmenování Excelovou tabulku, která odpovídá <xref:Microsoft.Office.Tools.Excel.ListObject>, název tabulky aplikace Excel se automaticky vrátí k původnímu názvu při uložení sešitu.  
  
## <a name="events"></a>Události  
 Tyto události jsou k dispozici pro <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Postupy: ověření dat při přidání nového řádku do ovládacího prvku ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Postupy: sloupců objektu ListObject Mapa k datům](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Postupy: výplň ListObject – ovládací prvky s daty](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
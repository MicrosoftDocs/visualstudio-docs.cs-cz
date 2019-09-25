---
title: ListObject – ovládací prvek
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b5286a4bddff2b529abd0a565bb4dbeef7ffaf3
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251870"
---
# <a name="listobject-control"></a>ListObject – ovládací prvek
  <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek je seznam, který zpřístupňuje události a může být svázán s daty. Když přidáte seznam do listu, Visual Studio vytvoří <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který lze programovat přímo bez nutnosti procházet systém Microsoft Office objektový model aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Vytvoření ovládacího prvku
 V projektech na úrovni dokumentu můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvky do listu v době návrhu nebo v době běhu. V projektech doplňku VSTO můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvky do listů pouze v době běhu. Další informace najdete v tématu [jak: Přidejte ovládací prvky ListObject do](../vsto/how-to-add-listobject-controls-to-worksheets.md)listů.

> [!NOTE]
> Ve výchozím nastavení se dynamicky vytvořené objekty seznamu neukládají v listu jako hostitelské ovládací prvky při zavření listu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek podporuje jednoduchou a složitou datovou vazbu. Ovládací prvek může být svázán se zdrojem dat <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> pomocí vlastností a <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> v době návrhu nebo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodou v době běhu. <xref:Microsoft.Office.Tools.Excel.ListObject>

> [!NOTE]
> Automaticky se aktualizuje, když je svázán se zdrojem dat, jako <xref:System.Data.DataTable>je například, který vyvolává události při změně dat. <xref:Microsoft.Office.Tools.Excel.ListObject> Pokud svážete <xref:Microsoft.Office.Tools.Excel.ListObject> se zdrojem dat, který nevyvolává události při změně dat, je nutné <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> zavolat metodu <xref:Microsoft.Office.Tools.Excel.ListObject>nebo <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> pro aktualizaci.

 Při přidání <xref:Microsoft.Office.Tools.Excel.ListObject> do buňky listu pomocí mapování opakujícího se elementu schématu na tuto buňku aplikace Visual Studio automaticky <xref:Microsoft.Office.Tools.Excel.ListObject> mapuje na vygenerovanou datovou sadu. <xref:Microsoft.Office.Tools.Excel.ListObject> Není však automaticky svázán s daty. Můžete provést kroky pro svázání <xref:Microsoft.Office.Tools.Excel.ListObject> s datovou sadou v době návrhu nebo v době běhu v projektu na úrovni dokumentu. Můžete programově navazovat <xref:Microsoft.Office.Tools.Excel.ListObject> na datovou sadu v době běhu v doplňku VSTO.

 Vzhledem k tomu <xref:Microsoft.Office.Tools.Excel.ListObject>, že jsou data oddělená od, byste měli přidat a odebrat data prostřednictvím vázané datové sady, a ne <xref:Microsoft.Office.Tools.Excel.ListObject>přímo přes. Pokud jsou data v vázané datové sadě aktualizována prostřednictvím libovolného mechanismu, <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek automaticky odráží změny. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek můžete rychle vyplnit vazbou <xref:Microsoft.Office.Tools.Excel.ListObject> na zdroj dat. Pokud data upravíte v datové vazbě <xref:Microsoft.Office.Tools.Excel.ListObject>, změny se automaticky provedou také ve zdroji dat. Pokud chcete vyplnit <xref:Microsoft.Office.Tools.Excel.ListObject> a pak uživateli povolit změnu dat v okně <xref:Microsoft.Office.Tools.Excel.ListObject> bez změny zdroje dat <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> , můžete použít metodu k odpojení <xref:Microsoft.Office.Tools.Excel.ListObject> od zdroje dat. Další informace najdete v tématu [jak: Naplní ovládací prvky ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)daty.

> [!NOTE]
> Datová vazba není podporována u překrývajících <xref:Microsoft.Office.Tools.Excel.ListObject> se ovládacích prvků.

### <a name="improve-performance-in-listobject-controls"></a>Zvýšení výkonu v ovládacích prvcích ListObject
 Čtení souboru XML do ovládacího prvku vázaného <xref:Microsoft.Office.Tools.Excel.ListObject> na data má za následek pomalejší, pokud ovládací prvek navážete jako první, a potom zavolejte <xref:System.Data.DataSet.ReadXml%2A> k vyplnění datové sady. Chcete-li zvýšit výkon <xref:System.Data.DataSet.ReadXml%2A> , zavolejte před vytvořením vazby ovládacího prvku.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Odpojit ovládací prvky ListObject ze zdroje dat
 Po vyplnění <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku daty jeho navázáním na zdroj dat ho můžete odpojit, aby změny provedené v datech v objektu list neovlivnily zdroj dat. Další informace najdete v tématu [jak: Naplní ovládací prvky ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)daty.

### <a name="restore-column-and-row-order"></a>Obnovit pořadí sloupců a řádků
 Při vytváření vazby dat k <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacímu prvku, který byl přidán do dokumentu v době návrhu, aplikace Visual Studio při každém uložení sešitu sleduje sloupec a pořadí řádků. Pokud uživatel během běhu přesune <xref:Microsoft.Office.Tools.Excel.ListObject> sloupce nebo řádky, nová objednávka se zachová při příštím otevření sešitu <xref:Microsoft.Office.Tools.Excel.ListObject> a ovládací prvek se znovu připojí ke zdroji dat.

 Chcete-li obnovit <xref:Microsoft.Office.Tools.Excel.ListObject> původní pořadí sloupců a řádků, můžete <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> zavolat metodu. Tato metoda odebere vlastnosti vlastního dokumentu související se zadaným <xref:Microsoft.Office.Tools.Excel.ListObject>pořadím sloupce a řádku. Tuto metodu zavolejte z <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> události sešitu, pokud nechcete zachovat pořadí <xref:Microsoft.Office.Tools.Excel.ListObject>sloupců a řádků.

## <a name="format"></a>Formát
 Formátování, které lze použít na objekt <xref:Microsoft.Office.Interop.Excel.ListObject> , lze použít <xref:Microsoft.Office.Tools.Excel.ListObject> pro ovládací prvek. To zahrnuje ohraničení, písma, formát čísel a styly. Koncoví uživatelé mohou změnit uspořádání sloupců v datové vazbě <xref:Microsoft.Office.Tools.Excel.ListObject>a tyto změny budou trvale provedeny s dokumentem, a to za předpokladu, že <xref:Microsoft.Office.Tools.Excel.ListObject> byl přidán do dokumentu v době návrhu. Při příštím otevření dokumentu bude objekt list svázán se stejným zdrojem dat, ale pořadí sloupců bude odrážet změny provedené uživateli.

## <a name="add-and-remove-columns-at-run-time"></a>Přidat a odebrat sloupce za běhu
 V ovládacím prvku vázaného <xref:Microsoft.Office.Tools.Excel.ListObject> na data nelze za běhu přidat ani odebrat sloupce. Pokud se koncový uživatel pokusí odstranit sloupec, bude okamžitě obnoven a všechny přidané sloupce budou odebrány. Proto je důležité napsat kód pro vysvětlení uživatelům, proč nemůže provádět tyto akce na objekt <xref:Microsoft.Office.Tools.Excel.ListObject> , který je vázán na data. Visual Studio poskytuje několik událostí <xref:Microsoft.Office.Tools.Excel.ListObject> souvisejících s datovou vazbou. Můžete například použít <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> událost, která upozorní uživatele, že data, která se pokusila o odstranění, nelze odstranit a že byla obnovena.

## <a name="add-and-remove-rows-at-run-time"></a>Přidat a odebrat řádky v době běhu
 Můžete ručně přidat a odebrat řádky v ovládacím prvku vázaného <xref:Microsoft.Office.Tools.Excel.ListObject> na data, pokud zdroj dat umožňuje přidání nových řádků a není jen pro čtení. Můžete napsat kód proti událostem, jako je <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> například, k ověření dat. Další informace najdete v tématu [jak: Ověří data při přidání nového řádku do ovládacího prvku](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)ListObject.

 V některých případech je relace objektu seznamu ke zdroji dat způsobena běžnými chybami. Například můžete namapovat <xref:Microsoft.Office.Tools.Excel.ListObject>, které sloupce se mají zobrazit v, takže pokud vynecháte sloupce, které mají omezení, například pole, které nemůže přijmout hodnoty null, jsou při každém vytvoření řádku vyvolány chyby. Můžete napsat kód pro přidání chybějících hodnot v obslužné rutině události pro <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> událost.

## <a name="rename-listobject-controls-in-excel"></a>Přejmenování ovládacích prvků ListObject v aplikaci Excel
 Aplikace Excel umožňuje uživatelům měnit názvy tabulek aplikace Excel v době běhu pomocí karty **Návrh** . <xref:Microsoft.Office.Tools.Excel.ListObject> Tento ovládací prvek však tuto funkci nepodporuje. Pokud se uživatel pokusí přejmenovat excelovou tabulku, která odpovídá <xref:Microsoft.Office.Tools.Excel.ListObject>, název tabulky aplikace Excel se při uložení sešitu automaticky vrátí k původnímu názvu.

## <a name="events"></a>Události
 Pro <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek jsou k dispozici následující události:

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Viz také:
- [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Postupy: Ověřit data při přidání nového řádku do ovládacího prvku ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Postupy: Mapování sloupců ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)
- [Postupy: Vyplnit ovládací prvky ListObject daty](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

---
title: 'Postupy: Naplnění dokumentů daty z databáze'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 907b3deeadd0a56f9e47a6e17a40579a0c9ffa64
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985888"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Postupy: Naplnění dokumentů daty z databáze

K datům v systém Microsoft Office projektech na úrovni dokumentu můžete přistupovat stejným způsobem jako při přístupu k datům v model Windows Formsch projektech. Pomocí stejných nástrojů a kódu můžete přenést data z databáze do vašeho řešení a pomocí ovládacího prvku model Windows Forms zobrazit data.

Kromě toho můžete zobrazit data pomocí hostitelských ovládacích prvků. Hostitelské ovládací prvky jsou nativní objekty v systém Microsoft Office Wordu, které byly vylepšeny pomocí událostí a schopností datových vazeb. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Následující příklad ukazuje, jak přidat ovládací prvky vázané na data v projektech na úrovni dokumentu pomocí návrháře. Příklad přidání ovládacích prvků vázaných na data v projektech doplňku VSTO za běhu najdete v tématu [Návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Související video ukázku naleznete v tématu [vázání dat na Word 2007 ovládací prvky obsahu pomocí Visual Studio Tools pro systém Office (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Přidání ovládacího prvku do dokumentu v době návrhu

### <a name="to-populate-a-document-with-data-from-a-database"></a>Naplnění dokumentu daty z databáze

1. Otevřete projekt na úrovni dokumentu aplikace Word v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]s dokumentem otevřeným v návrháři.

2. Otevřete okno **zdroje dat** a vytvořte zdroj dat z databáze. Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

3. Přetáhněte pole, které chcete, z okna **zdroje dat** do dokumentu.

Do dokumentu se přidá ovládací prvek obsahu. Typ ovládacího prvku obsahu závisí na datovém typu pole, které jste vybrali. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

Můžete přidat jiný ovládací prvek tak, že vyberete datové pole v okně **zdroje dat** a potom v rozevíracím seznamu vyberete jiný ovládací prvek.

## <a name="objects-in-the-project"></a>Objekty v projektu

Kromě ovládacího prvku jsou do projektu automaticky přidány následující objekty související s daty:

- Typová datová sada, která zapouzdřuje tabulky dat, ke kterým jste se připojili v databázi. Další informace najdete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- <xref:System.Windows.Forms.BindingSource>, který spojuje ovládací prvek s typovou datovou sadou. Další informace najdete v tématu [Přehled komponent BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, který připojuje typovou datovou sadu k databázi. Další informace najdete v tématu [Vytvoření a konfigurace objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

- TableAdapterManager, který se používá ke koordinaci tabulkových adaptérů v datové sadě za účelem povolení hierarchických aktualizací. Další informace najdete v tématu [Hierarchická aktualizace](../data-tools/hierarchical-update.md) a [TableAdapterManager reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Při spuštění projektu ovládací prvek zobrazí první záznam ve zdroji dat. Pomocí <xref:System.Windows.Forms.BindingSource> můžete uživatelům umožnit procházení záznamů.

### <a name="to-scroll-through-the-records"></a>Procházení záznamů

- Použijte <xref:System.Windows.Forms.BindingSource> metody, jako je <xref:System.Windows.Forms.BindingSource.MoveNext%2A> a <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informace o tom, jak odeslat aktualizace typové datové sadě a databázi, naleznete v tématu [How to: Update a data source to data z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Viz také:

- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Přehled použití místních souborů databáze v řešeních pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
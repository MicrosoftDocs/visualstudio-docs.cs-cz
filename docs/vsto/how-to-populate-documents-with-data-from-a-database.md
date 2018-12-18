---
title: 'Postupy: naplnění dokumentů daty z databáze'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af068fc9cdacc0f681232ee4c7424d67d77f3a11
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756798"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Postupy: naplnění dokumentů daty z databáze

Stejným způsobem, že vám přístup k datům ve Windows Forms projekty můžou k datům ve projekty na úrovni dokumentu pro Microsoft Office. Použít stejnou nástroje a kódu přenést data z databáze do vašeho řešení a ovládací prvky Windows Forms můžete použít k zobrazení dat.

Kromě toho můžete zobrazit data pomocí hostitelské ovládací prvky. Hostitelské ovládací prvky jsou nativní objekty v aplikaci Microsoft Office Word, které vylepšily se události a možnosti data vazby. Další informace najdete v tématu [hostitele položky a hostitelem Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Následující příklad ukazuje, jak přidat ovládací prvky vázané na data v projekty na úrovni dokumentu pomocí návrháře. Příklad toho, jak přidat ovládací prvky vázané na data v projekty doplňku VSTO za běhu, naleznete v části [návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související Videoukázka, najdete v části [vazby dat do Wordu 2007 obsah ovládací prvky pomocí nástrojů Visual Studio Tools pro systém Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Přidání ovládacího prvku na dokument v době návrhu

### <a name="to-populate-a-document-with-data-from-a-database"></a>K naplnění dokumentů daty z databáze

1.  Otevřete projekt na úrovni dokumentu aplikace Word v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], se dokument otevřít v návrháři.

2.  Otevřete **zdroje dat** okno a vytvořte zdroj dat z databáze. Další informace najdete v tématu [přidat nová připojení](../data-tools/add-new-connections.md).

3.  Přetáhněte pole ze **zdroje dat** okna dokumentu.

Ovládací prvek obsahu se přidá do dokumentu. Typ obsahu ovládacího prvku, závisí na datový typ pole, které jste vybrali. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

Různé ovládacího prvku můžete přidat výběrem datové pole v **zdroje dat** okna a pak vyberete různé ovládací prvek z rozevíracího seznamu.

## <a name="objects-in-the-project"></a>Objekty v projektu

Kromě ovládacího prvku jsou automaticky přidány následující data související s objekty do projektu:

-   Typové datové sady, který zapouzdřuje datových tabulek, které jste připojeni k v databázi. Další informace najdete v tématu [datové sady nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   A <xref:System.Windows.Forms.BindingSource> ovládacího prvku která se připojuje k typové datové sady. Další informace najdete v tématu [BindingSource – přehled komponenty](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   TableAdapter, která se připojuje k databázi typové datové sady. Další informace najdete v tématu [vytvořit a nakonfigurovat TableAdapters](../data-tools/create-and-configure-tableadapters.md).

-   TableAdapterManager, který se používá ke koordinaci adaptéry tabulek v datové sadě umožňující hierarchické aktualizace. Další informace najdete v tématu [hierarchické aktualizace](../data-tools/hierarchical-update.md) a [TableAdapterManager odkaz](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Při spuštění projektu zobrazí ovládací prvek ve zdroji dat na první záznam. Můžete použít <xref:System.Windows.Forms.BindingSource> umožňuje uživatelům procházet záznamů.

### <a name="to-scroll-through-the-records"></a>Chcete-li procházet záznamů

-   Použití <xref:System.Windows.Forms.BindingSource> metody, jako <xref:System.Windows.Forms.BindingSource.MoveNext%2A> a <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informace o tom, jak odesílání aktualizací na typové datové sady a databáze najdete v tématu [postup: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Viz také:

- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Použití místních souborů databáze v přehled řešení pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource – přehled komponenty](/dotnet/framework/winforms/controls/bindingsource-component-overview)
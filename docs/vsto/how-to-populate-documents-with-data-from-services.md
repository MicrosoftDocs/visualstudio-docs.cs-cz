---
title: 'Postupy: Naplnění dokumentů daty ze služeb'
description: Zjistěte, jak můžete použít data ze služeb ve vašem řešení a jak můžete pomocí model Windows Forms ovládací prvky zobrazit data v dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4d8fb377896762672574c6ef5ff15b4e12b9e59
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845827"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Postupy: Naplnění dokumentů daty ze služeb

Přístup k datům funguje stejným způsobem v projektech na úrovni dokumentu pro systém Microsoft Office stejně jako v model Windows Formsch projektech. Můžete použít stejné nástroje a kód k přenesení dat do vašeho řešení a můžete dokonce použít ovládací prvky model Windows Forms k zobrazení dat. Kromě toho můžete využít ovládací prvky označované jako hostitelské ovládací prvky, které jsou nativní objekty v systém Microsoft Office Excel a systém Microsoft Office Word, které byly vylepšeny s událostmi a funkcemi vazby dat. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Následující příklad ukazuje, jak přidat ovládací prvky vázané na data do dokumentů v době návrhu. Příklad přidání ovládacích prvků vázaných na data v doplňcích VSTO za běhu najdete v tématu [Návod: vytvoření vazby na data ze služby v projektu doplňku VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Naplnění projektu na úrovni dokumentu daty z webové služby

1. Otevřete okno **zdroje dat** a vytvořte zdroj dat služby pro svůj projekt. Další informace najdete v tématu [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md).

2. Přetáhněte tabulku nebo pole z okna **zdroje dat** do dokumentu.

     V dokumentu je vytvořen ovládací prvek, který je <xref:System.Windows.Forms.BindingSource> vázán na třídu objektu v projektu a třídy jsou vygenerovány pro službu.

3. Ve svém kódu vytvořte instanci třídy webové služby, ke které jste se připojili v kroku 1.

4. Pokud existují vlastnosti, které jsou požadovány pro komunikaci s webovou službou, vytvořte instance těchto vlastností.

5. Vytvořte a odešlete požadavek na data pomocí metod vydaných webovou službou a všemi instancemi vlastností, které jste vytvořili v kroku 4.

     Metody, které použijete, závisí na tom, co webová služba nabízí.

6. Přiřaďte odpověď na data z webové služby k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> .

Při spuštění projektu ovládací prvky zobrazí první záznam ve zdroji dat. Můžete povolit procházení záznamů prostřednictvím zpracování událostí měny pomocí objektů v <xref:System.Windows.Forms.BindingSource> .

## <a name="see-also"></a>Viz také

- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
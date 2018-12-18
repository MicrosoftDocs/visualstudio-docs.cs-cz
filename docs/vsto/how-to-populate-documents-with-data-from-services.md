---
title: 'Postupy: naplnění dokumentů daty ze služeb'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758539"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Postupy: naplnění dokumentů daty ze služeb

Přístup k datům funguje stejným způsobem jako v projekty na úrovni dokumentu pro Microsoft Office jako v systému Windows Forms projekty. Použít stejnou nástroje a kódu přenést data do vašeho řešení a ovládací prvky Windows Forms můžete použít i k zobrazení dat. Kromě toho můžete využít názvem hostitelské ovládací prvky, které jsou nativní objekty v aplikaci Microsoft Office Excel a Microsoft Office Word vylepšily se události a možnosti data vazba ovládacích prvků. Další informace najdete v tématu [hostitele položky a hostitelem Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Následující příklad ukazuje, jak přidat ovládací prvky vázané na data do dokumentů v době návrhu. Příklad, jak přidat ovládací prvky vázané na data v doplňcích VSTO za běhu, naleznete v části [návod: vytvoření vazby na data ze služby v projektu doplňku VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související Videoukázka, najdete v části [jak I: interakci s webovými službami z aplikace Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>K naplnění projekt na úrovni dokumentu a s daty z webové služby

1.  Otevřete **zdroje dat** okno a vytvořte zdroj dat služby pro váš projekt. Další informace najdete v tématu [přidat nové zdroje dat](../data-tools/add-new-data-sources.md).

2.  Přetáhněte tabulku nebo pole, které chcete z **zdroje dat** okna dokumentu.

     Vytvoření ovládacího prvku v dokumentu, <xref:System.Windows.Forms.BindingSource> se vytvoří, je vázán k třídu objektu ve vašem projektu a se generují třídy pro službu.

3.  V kódu vytvoření instance třídy webové služby, která je připojena k v kroku 1.

4.  Pokud existují vlastnosti, které jsou požadovány pro komunikaci s webovou službu, vytvořte instance tyto vlastnosti.

5.  Vytvoření a odeslání požadavku na data pomocí metody vystavené webové služby a všechny instance vlastnost, že kterou jste vytvořili v kroku 4.

     Metody, které používáte závisí na jaké webovou službu nabízí.

6.  Přiřadit odpovědi data z webovou službu, která <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource>.

Při spuštění projektu ovládací prvky zobrazení ve zdroji dat na první záznam. Posouvání záznamů událostí měny pomocí objektů v můžete povolit <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Viz také:

- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
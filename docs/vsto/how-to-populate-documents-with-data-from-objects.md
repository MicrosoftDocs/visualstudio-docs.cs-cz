---
title: 'Postupy: Naplnění dokumentů daty z objektů'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38461fc30f71a811033ea70bfe560a6492f56e12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547170"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Postupy: Naplnění dokumentů daty z objektů

K přístupu k datům v datovém objektu funguje stejným způsobem v projektech na úrovni dokumentu systém Microsoft Office Word, jako v model Windows Formsch projektech. Pomocí stejných nástrojů a kódu můžete přenést data z objektu do vašeho řešení a pomocí model Windows Forms ovládací prvky zobrazíte data. Kromě toho můžete zobrazit data pomocí hostitelských ovládacích prvků. Hostitelské ovládací prvky jsou nativní objekty v systém Microsoft Office Wordu, které byly vylepšeny pomocí událostí a schopností datových vazeb. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

K naplnění dokumentu daty z objektu je nutné provést tři základní kroky:

- Přidejte do dokumentu ovládací prvek, který lze vytvořit s daty.

- Přidejte datový objekt do dokumentu.

- Připojte datový objekt k objektu BindingSource.

## <a name="to-add-a-data-object"></a>Přidání datového objektu

Chcete-li přidat datový objekt, otevřete okno **zdroje dat** a vytvořte zdroj dat z objektu. Další informace najdete v tématu [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Připojit datový objekt k objektu BindingSource

V projektech na úrovni dokumentu přidáte ovládací prvky do dokumentu a svážete je s daty v době návrhu.

V projektech doplňku VSTO vytvoříte ovládací prvky a svážete je v době běhu.

### <a name="document-level-projects"></a>Projekty na úrovni dokumentu

Připojení datového objektu k objektu BindingSource:

1. Přetáhněte datové pole, které chcete, z okna **zdroje dat** do dokumentu. Tím se automaticky vytvoří ovládací prvek.

2. V kódu vytvořte instanci typu objektu, který jste zvolili pro zdroj dat.

3. Přiřaďte instanci k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> .

### <a name="application-level-projects"></a>Projekty na úrovni aplikace

Připojení datového objektu k objektu BindingSource:

1. V kódu vytvořte instanci typu objektu, který je přidružen ke zdroji dat.

2. Vytvořte instanci objektu <xref:System.Windows.Forms.BindingSource>.

3. Přiřaďte instanci zdroje dat k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> .

4. Přidejte zdroj dat jako datovou vazbu k ovládacímu prvku.

## <a name="see-also"></a>Viz také

- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
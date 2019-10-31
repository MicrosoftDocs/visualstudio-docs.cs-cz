---
title: 'Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 551d27cf8d40f2e6e9c996b031fa6c4e0a233355
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189573"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru
  Můžete označit datovou položku, která se uloží do mezipaměti v dokumentu, aby byla dostupná offline. To také umožňuje, aby data v dokumentu byla zpracována jiným kódem při uložení dokumentu na server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Můžete označit datovou položku, která má být uložena do mezipaměti, je-li datová položka deklarována v kódu, nebo pokud používáte <xref:System.Data.DataSet>, nastavením vlastnosti v okně **vlastnosti** . Pokud ukládáte do mezipaměti datovou položku, která není <xref:System.Data.DataSet> ani <xref:System.Data.DataTable>, zajistěte, aby splňovala kritéria pro ukládání do mezipaměti v dokumentu. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

> [!NOTE]
> Datové sady vytvořené pomocí Visual Basic, které jsou označené jako **mezipaměti** a **WithEvents** (včetně datových sad, které jsou přetažené z okna **zdroje dat** nebo **sady nástrojů** , které mají vlastnost **CacheInDocument** nastavenou na **hodnotu true** ) mají podtržítka s předponou a jejich názvy v mezipaměti. Například pokud vytvoříte datovou sadu a pojmenujte ji **zákazníci**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> název bude v mezipaměti **_Customers** . Když použijete <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> k přístupu k této položce v mezipaměti, musíte místo **zákazníků**zadat **_Customers** .

### <a name="to-cache-data-in-the-document-using-code"></a>Ukládání dat do mezipaměti v dokumentu pomocí kódu

1. Deklarujte veřejné pole nebo vlastnost pro datovou položku jako člena třídy položky hostitele ve vašem projektu, jako je například třída `ThisDocumen`t ve wordovém projektu nebo třída `ThisWorkbook` v projektu aplikace Excel.

2. Použijte atribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> pro člena k označení datové položky, která má být uložena v mezipaměti dat dokumentu. Následující příklad aplikuje tento atribut na deklaraci pole pro <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Přidejte kód pro vytvoření instance datové položky a v případě potřeby pro načtení z databáze.

     Datová položka je načtena pouze při prvním vytvoření; poté mezipaměť zůstává s dokumentem a Vy musíte napsat jiný kód pro jeho aktualizaci.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Mezipaměť datové sady v dokumentu pomocí okno Vlastnosti

1. Přidejte do projektu datovou sadu pomocí nástrojů v návrháři sady Visual Studio, například přidáním zdroje dat do projektu pomocí okna **zdroje dat** .

2. Vytvořte instanci sady dat, pokud ji ještě nemáte, a vyberte instanci v návrháři.

3. V okně **vlastnosti** nastavte vlastnost **CacheInDocument** na **hodnotu true**.

     Další informace najdete v tématu [vlastnosti v projektech Office](../vsto/properties-in-office-projects.md).

4. V okně **vlastnosti** nastavte vlastnost **modifikátory** na hodnotu **Public** (ve výchozím nastavení je to **interní**).

## <a name="see-also"></a>Viz také:
- [Data mezipaměti](../vsto/caching-data.md)
- [Postupy: ukládání zdroje dat v dokumentu Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md)
- [Uložit data](../data-tools/save-data-back-to-the-database.md)

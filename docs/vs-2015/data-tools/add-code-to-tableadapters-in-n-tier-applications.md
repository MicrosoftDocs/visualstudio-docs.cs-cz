---
title: Přidání kódu do objekty TableAdapter v n-vrstvých aplikacích | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673106"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete roztáhnout funkce, a to `TableAdapter` tak, že vytvoříte soubor částečné třídy pro `TableAdapter` a přidáte do něj kód (místo přidávání kódu do vlastnosti *DataSet*. Soubor DataSet. Designer). Částečné třídy umožňují, aby kód pro konkrétní třídu byl rozdělen mezi několik fyzických souborů. Další informace naleznete v tématu [částečný](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) nebo [částečný (typ)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Kód, který definuje a `TableAdapter` je generován při každém provedení změny v `TableAdapter` . Tento kód je generován také v případě, že se změny provedou při spuštění libovolného průvodce, který upraví konfiguraci `TableAdapter` . Chcete-li zabránit odstranění kódu během obnovování `TableAdapter` , přidejte kód do souboru dílčí třídy `TableAdapter` .

 Ve výchozím nastavení platí, že po oddělení datové sady a `TableAdapter` kódu je výsledkem diskrétní soubor třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DataSet*. Designer. vb (nebo *DataSet*. Designer.cs) obsahující `TableAdapter` kód. Projekt, který je určen vlastností **projektu DataSet** , má soubor s názvem *DataSet*. DataSet. Designer. vb (nebo *DataSet*. DataSet.Designer.cs), která obsahuje kód datové sady.

> [!NOTE]
> Při oddělení datových sad a `TableAdapter` s (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné přesunout ručně do projektu datové sady.

> [!NOTE]
> Návrhář DataSet poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužné rutiny událostí, pokud je vyžadováno ověření. Další informace najdete v tématu [Přidání ověřování do n-vrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Přidání uživatelského kódu do TableAdapter v n-vrstvé aplikaci

1. Vyhledejte projekt, který obsahuje soubor. XSD (datovou sadu).

2. Dvojím kliknutím na soubor **. xsd** otevřete datovou sadu.

3. Klikněte pravým tlačítkem na `TableAdapter` , do kterého chcete přidat kód, a pak vyberte**Zobrazit kód**.

     Je vytvořena částečná třída, která se otevře v editoru kódu.

4. Přidejte kód do deklarace částečné třídy.

5. Následující příklad ukazuje, kde přidat kód do `CustomersTableAdapter` v `NorthwindDataSet` :

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Viz také
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md) [Přidání kódu do datových sad v n-vrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [objekty TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) přehled [hierarchické aktualizace](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6) [TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
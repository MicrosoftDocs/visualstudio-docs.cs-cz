---
title: Přidání kódu do datových sad v n vrstvé aplikace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48f27d2e1bb72b7c5c0aaf1a66673beae003dd66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202212"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Přidávání kódu do datových sad ve vícevrstvých aplikacích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Funkce pro datovou sadu můžete rozšířit vytvořením souboru částečné třídy datové sady a přidáním kódu k němu (místo přidání kódu *DatasetName*. Soubor Dataset.Designer). Částečné třídy povolit kód pro konkrétní třídu rozdělit mezi několik fyzických souborů. Další informace najdete v tématu [částečné](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) nebo [částečné třídy a metody](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
 Kód, který definuje datovou sadu je generována pokaždé, když dojde ke změně definice datové sady (v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md)). Tento kód se také vygeneruje, když provedete změny za běhu všechny průvodce, který upraví konfiguraci datové sady. Aby váš kód odstranit během obnovování datové sady, přidejte kód do souboru částečné třídy datové sady.  
  
 Ve výchozím nastavení po oddělíte datové sady a `TableAdapter` kód, výsledek je soubor samostatné třídy v každém projektu. Původní projekt má filenamed *DatasetName*. Designer.vb (nebo *DatasetName*. Designer.cs), který obsahuje `TableAdapter` kódu. Projekt, který je zadaný ve **projektu Dataset** vlastnost má soubor s názvem *DatasetName*. DataSet.Designer.vb (nebo *DatasetName*. DataSet.Designer.cs). Tento soubor obsahuje kód, datové sady.  
  
> [!NOTE]
>  Když oddělíte datové sady a `TableAdapter`s (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné ručně přesunout do projektu datové sady.  
  
> [!NOTE]
>  Když kód pro ověření musí být přidán, [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md)poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužných rutin událostí. Další informace najdete v tématu [přidání ověřování do vícevrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Přidání kódu do datových sad v n vrstvé aplikace  
  
1.  Najít projekt, který obsahuje soubor XSD ( [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Vyberte **XSD** soubor otevřete [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Klikněte pravým tlačítkem na tabulku dat, ke kterému chcete přidat kód (název tabulky v záhlaví okna) a thenselect**zobrazit kód**.  
  
     Částečné třídy se vytvoří a otevře v editoru kódu.  
  
4.  Přidejte kód do částečné deklarace třídy.  
  
     Následující příklad ukazuje, kde přidat kód CustomersDataTable v NorthwindDataSet:  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)   
 [Přidejte kód do prvků TableAdapters ve víceúrovňových aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [Objekty TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager – přehled](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Přehled hierarchické aktualizace](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Vytváření datových aplikací](../data-tools/creating-data-applications.md)   
 [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)


---
title: Rozšíření funkcí objektů TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 34a5c1601071a36ca11005503e2f443a72ca3dfe
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586637"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozšíření funkcí objektů TableAdapter

Můžete roztáhnout funkci TableAdapter přidáním kódu do souboru částečné třídy TableAdapter.

Kód, který definuje TableAdapter, se znovu vygeneruje, když se provedou jakékoli změny TableAdapter v **Návrhář datových sad**, nebo když Průvodce upraví konfiguraci TableAdapter. Chcete-li zabránit odstranění kódu během obnovování TableAdapter, přidejte kód do souboru částečné třídy TableAdapter.

Částečné třídy umožňují, aby byl kód pro konkrétní třídu rozdělen mezi více fyzických souborů. Další informace naleznete v tématu [částečný](/dotnet/visual-basic/language-reference/modifiers/partial) nebo [částečný (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Hledání objekty TableAdapter v kódu

I když jsou objekty TableAdapter vytvořeny pomocí **Návrhář datových sad**, třídy TableAdapter, které jsou generovány, nejsou vnořené třídy <xref:System.Data.DataSet>. Objekty TableAdapter se nachází v oboru názvů na základě názvu přidružené datové sady TableAdapter. Například pokud vaše aplikace obsahuje datovou sadu s názvem `HRDataSet`, objekty TableAdapter by se nacházela v oboru názvů `HRDataSetTableAdapters`. (Konvence pojmenování se řídí tímto vzorem: *dataset* + `TableAdapters`).

Následující příklad předpokládá, že TableAdapter s názvem `CustomersTableAdapter`je v projektu s `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Vytvoření částečné třídy pro TableAdapter

1. Přejděte do nabídky **projekt** a vyberte **Přidat třídu**a přidejte do projektu novou třídu.

2. Pojmenujte `CustomersTableAdapterExtended`třídy.

3. Vyberte **Přidat**.

4. Nahraďte kód správným oborem názvů a názvem částečné třídy pro váš projekt následujícím způsobem:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Viz také:

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

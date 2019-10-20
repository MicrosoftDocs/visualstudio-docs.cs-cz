---
title: Rozšiřování funkcí TableAdapter | Microsoft Docs
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672359"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozšíření funkcí objektů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete roztáhnout funkci TableAdapter přidáním kódu do souboru částečné třídy TableAdapter.

 Kód, který definuje TableAdapter, se znovu vygeneruje, když se provedou jakékoli změny TableAdapter v **Návrhář datových sad**, nebo když Průvodce upraví konfiguraci TableAdapter. Chcete-li zabránit odstranění kódu během obnovování TableAdapter, přidejte kód do souboru částečné třídy TableAdapter.

 Částečné třídy umožňují, aby byl kód pro konkrétní třídu rozdělen mezi více fyzických souborů. Další informace naleznete v tématu [částečný](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) nebo [částečný (typ)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Hledání objekty TableAdapter v kódu
 I když jsou objekty TableAdapter vytvořeny pomocí **Návrhář datových sad**, třídy TableAdapter, které jsou generovány, nejsou vnořené třídy <xref:System.Data.DataSet>. Objekty TableAdapter se nachází v oboru názvů na základě názvu přidružené datové sady TableAdapter. Například pokud vaše aplikace obsahuje datovou sadu s názvem `HRDataSet`, objekty TableAdapter by se nacházela v oboru názvů `HRDataSetTableAdapters`. (Konvence pojmenování se řídí tímto vzorem: *dataset*  +  `TableAdapters`).

 Následující příklad předpokládá, že TableAdapter s názvem `CustomersTableAdapter`is v projektu s `NorthwindDataSet`.

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Vytvoření částečné třídy pro TableAdapter

1. Přejděte do nabídky **projekt** a vyberte**Přidat třídu**a přidejte do projektu novou třídu.

2. Pojmenujte `CustomersTableAdapterExtended` třídy.

3. Vyberte **Přidat**.

4. Nahraďte kód správným oborem názvů a názvem částečné třídy pro váš projekt následujícím způsobem:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Viz také
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

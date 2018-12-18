---
title: Rozšíření funkcí TableAdapter | Dokumentace Microsoftu
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58f92f082ec4e7934e8eb7597832a6a58d23a1ca
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219741"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozšíření funkcí objektů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Funkce objektu typu TableAdapter můžete rozšířit přidáním kódu do souboru částečné třídy TableAdapter.  
  
 Při jakékoli změně TableAdapter v se znovu vygeneroval kód, který definuje objektu typu TableAdapter **Návrhář Dataset**, nebo když průvodce změní konfiguraci objektu TableAdapter. Abyste zabránili odstranění při generování objektu TableAdapter kódu, přidejte kód do souboru částečné třídy TableAdapter.  
  
 Částečné třídy povolit kód pro konkrétní třídu rozdělit mezi několik fyzických souborů. Další informace najdete v tématu [částečné](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) nebo [partial (typ)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Najít objekty TableAdapter v kódu  
 Zatímco objekty TableAdapter jsou navrženy s **Návrhář Dataset**, generované třídy TableAdapter nejsou vnořené třídy typu <xref:System.Data.DataSet>. Objekty TableAdapter jsou umístěny v oboru názvů na základě názvu objektu TableAdapter přidružený objekt dataset. Například, pokud vaše aplikace obsahuje datovou sadu s názvem `HRDataSet`, objekty TableAdapter by být umístěný ve `HRDataSetTableAdapters` oboru názvů. (Tento vzor dodržuje zásady vytváření názvů: *DatasetName* + `TableAdapters`).  
  
 V následujícím příkladu se předpokládá TableAdapter s názvem `CustomersTableAdapter`nachází v projektu s `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Chcete-li vytvořit částečné třídy objektu TableAdapter  
  
1.  Přidejte novou třídu do projektu tak, že přejdete **projektu** nabídky a vyberete**přidat třídu**.  
  
2.  Název třídy `CustomersTableAdapterExtended`.  
  
3.  Vyberte **přidat**.  
  
4.  Nahraďte kód správný obor názvů a název dílčí třídy pro váš projekt následujícím způsobem:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)


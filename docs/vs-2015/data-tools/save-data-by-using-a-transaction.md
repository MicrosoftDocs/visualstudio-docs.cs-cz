---
title: Ukládání dat pomocí transakce | Dokumentace Microsoftu
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c73dd654a2d48be963e592d94685c74d3a16057
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219572"
---
# <a name="save-data-by-using-a-transaction"></a>Ukládání dat pomocí transakce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ukládání dat v transakci pomocí <xref:System.Transactions> oboru názvů. Použití <xref:System.Transactions.TransactionScope> objektu k účasti v transakci, která se automaticky spravuje za vás.  
  
 Projekty nejsou vytvořeny pomocí odkazu na sestavení System.Transactions, je třeba ručně přidat odkaz na projektech, které používají transakce.  
  
> [!NOTE]
>  <xref:System.Transactions> Obor názvů je podporován v systému Windows 2000 nebo novější.  
  
 Nejjednodušší způsob, jak implementovat transakce je k vytvoření instance <xref:System.Transactions.TransactionScope> objekt `using` příkazu. (Další informace najdete v tématu [příkazu Using](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), a [příkaz using](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Kód, který běží v rámci `using` příkaz účastní v transakci.  
  
 Chcete-li zapsat transakci, zavolejte <xref:System.Transactions.TransactionScope.Complete%2A> metody jako poslední příkaz v pomocí blokovat.  
  
 Chcete-li vrátit zpět transakci, vyvolat výjimku před voláním <xref:System.Transactions.TransactionScope.Complete%2A> metody.  
  
 Další informace najdete v tématu [uložit data v rámci transakce](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Chcete-li přidat odkaz na knihovnu dll System.Transactions  
  
1.  Na **projektu** nabídce vyberte možnost **přidat odkaz**.  
  
2.  Na **.NET** kartu (**systému SQL Server** kartu pro projekty na SQL serveru) vyberte **System.Transactions**a pak vyberte **OK**.  
  
     Odkaz na System.Transactions.dll je přidá do projektu.  
  
### <a name="to-save-data-in-a-transaction"></a>Chcete-li uložit data v transakci  
  
-   Přidejte kód pro uložení dat v rámci nástroje pomocí příkazu, který obsahuje transakci. Následující kód ukazuje, jak vytvořit a vytvoření instance <xref:System.Transactions.TransactionScope> objektu v pomocí příkazu:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)


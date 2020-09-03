---
title: Uložení dat pomocí transakce | Microsoft Docs
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652836"
---
# <a name="save-data-by-using-a-transaction"></a>Ukládání dat pomocí transakce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data uložíte v transakci pomocí <xref:System.Transactions> oboru názvů. Použijte <xref:System.Transactions.TransactionScope> objekt k účasti v transakci, která je pro vás automaticky spravovaná.

 Projekty nejsou vytvořeny s odkazem na sestavení System. Transactions, takže je nutné ručně přidat odkaz na projekty, které používají transakce.

> [!NOTE]
> <xref:System.Transactions>Obor názvů je podporován ve Windows 2000 nebo novějším.

 Nejjednodušší způsob, jak implementovat transakci, je vytvořit instanci <xref:System.Transactions.TransactionScope> objektu v `using` příkazu. (Další informace naleznete v tématu [using](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)a [using Statement](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Kód, který je spuštěn v `using` příkazu, se účastní transakce.

 Chcete-li transakci potvrdit, zavolejte <xref:System.Transactions.TransactionScope.Complete%2A> metodu jako poslední příkaz v bloku using.

 Chcete-li transakci vrátit zpět, vyvolejte výjimku před voláním <xref:System.Transactions.TransactionScope.Complete%2A> metody.

 Další informace najdete v tématu [uložení dat v transakci](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Přidání odkazu na knihovnu DLL System. Transactions

1. V nabídce **projekt** vyberte možnost **Přidat odkaz**.

2. Na kartě **.NET** (**SQL Server** pro SQL Server projekty) vyberte **System. Transactions**a pak vyberte **OK**.

     Do projektu se přidá odkaz na System.Transactions.dll.

### <a name="to-save-data-in-a-transaction"></a>Uložení dat v transakci

- Přidejte kód pro uložení dat v rámci příkazu Using, který obsahuje transakci. Následující kód ukazuje, jak vytvořit a vytvořit instanci <xref:System.Transactions.TransactionScope> objektu v příkazu Using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

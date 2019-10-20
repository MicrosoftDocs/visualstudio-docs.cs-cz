---
title: 'Postupy: ukládání dat pomocí transakce'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641314"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Postupy: ukládání dat pomocí transakce

Data uložíte v transakci pomocí <xref:System.Transactions> oboru názvů. K účasti v transakci, která je pro vás automaticky spravovaná, použijte objekt <xref:System.Transactions.TransactionScope>.

Projekty nejsou vytvořeny s odkazem na sestavení *System. Transactions* , takže je nutné ručně přidat odkaz na projekty, které používají transakce.

Nejjednodušší způsob, jak implementovat transakci, je vytvořit instanci objektu <xref:System.Transactions.TransactionScope> v příkazu `using`. (Další informace naleznete v tématu [using](/dotnet/visual-basic/language-reference/statements/using-statement)a [using Statement](/dotnet/csharp/language-reference/keywords/using-statement).) Kód, který je spuštěn v rámci příkazu `using`, se účastní transakce.

Chcete-li transakci potvrdit, zavolejte metodu <xref:System.Transactions.TransactionScope.Complete%2A> jako poslední příkaz v bloku using.

Chcete-li transakci vrátit zpět, vyvolejte výjimku před voláním metody <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Přidání odkazu na System. Transactions. dll

1. V nabídce **projekt** vyberte možnost **Přidat odkaz**.

2. Na kartě **.NET** (**SQL Server** pro SQL Server projekty) vyberte **System. Transactions**a pak vyberte **OK**.

     Do projektu se přidá odkaz na *System. Transactions. dll* .

## <a name="to-save-data-in-a-transaction"></a>Uložení dat v transakci

- Přidejte kód pro uložení dat v rámci příkazu Using, který obsahuje transakci. Následující kód ukazuje, jak vytvořit a vytvořit instanci objektu <xref:System.Transactions.TransactionScope> v příkazu Using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
- [Návod: Uložení dat do transakce](../data-tools/save-data-in-a-transaction.md)
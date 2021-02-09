---
title: 'Postupy: ukládání dat pomocí transakce'
description: Přečtěte si, jak uložit data pomocí transakce s nástroji datové sady v sadě Visual Studio. Data uložíte v transakci pomocí oboru názvů System. Transactions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c633ed01821f500e958d3c7549febc23cf33c09d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858485"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Postupy: ukládání dat pomocí transakce

Data uložíte v transakci pomocí <xref:System.Transactions> oboru názvů. Použijte <xref:System.Transactions.TransactionScope> objekt k účasti v transakci, která je pro vás automaticky spravovaná.

Projekty nejsou vytvořeny s odkazem na sestavení *System. Transactions* , takže je nutné ručně přidat odkaz na projekty, které používají transakce.

Nejjednodušší způsob, jak implementovat transakci, je vytvořit instanci <xref:System.Transactions.TransactionScope> objektu v `using` příkazu. (Další informace naleznete v tématu [using](/dotnet/visual-basic/language-reference/statements/using-statement)a [using Statement](/dotnet/csharp/language-reference/keywords/using-statement).) Kód, který je spuštěn v `using` příkazu, se účastní transakce.

Chcete-li transakci potvrdit, zavolejte <xref:System.Transactions.TransactionScope.Complete%2A> metodu jako poslední příkaz v bloku using.

Chcete-li transakci vrátit zpět, vyvolejte výjimku před voláním <xref:System.Transactions.TransactionScope.Complete%2A> metody.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Přidání odkazu na System.Transactions.dll

1. V nabídce **projekt** vyberte možnost **Přidat odkaz**.

2. Na kartě **.NET** (**SQL Server** pro SQL Server projekty) vyberte **System. Transactions** a pak vyberte **OK**.

     Do projektu se přidá odkaz na *System.Transactions.dll* .

## <a name="to-save-data-in-a-transaction"></a>Uložení dat v transakci

- Přidejte kód pro uložení dat v rámci příkazu Using, který obsahuje transakci. Následující kód ukazuje, jak vytvořit a vytvořit instanci <xref:System.Transactions.TransactionScope> objektu v příkazu Using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
- [Návod: Uložení dat do transakce](../data-tools/save-data-in-a-transaction.md)

---
title: Dědičnost datových tříd (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e7dfc2b1137b30a03425f663d70e12c528dad39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657403"
---
# <a name="data-class-inheritance-or-designer"></a>Dědičnost datových tříd (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stejně jako jiné objekty [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] mohou třídy použít dědičnost a být odvozeny od jiných tříd. V kódu můžete určit vztahy dědičnosti mezi objekty tím, že deklarujete, že jedna třída dědí z jiné třídy. V databázi jsou vztahy dědičnosti vytvářeny několika způsoby. Rozhraní [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) podporuje koncept dědičnosti jedné tabulky, protože je často implementován v relačních systémech.

 V případě dědičnosti s jednou tabulkou existuje jedna databázová tabulka, která obsahuje sloupce pro základní i odvozené třídy. U relačních dat obsahuje sloupec diskriminátor hodnotu, která určuje, do které třídy daný záznam patří. Představte si třeba tabulku osob, která obsahuje všechny zaměstnané společnosti. Někteří lidé jsou zaměstnanci a někteří lidé jsou manažeři. Tabulka osob obsahuje sloupec s názvem Type, který má hodnotu 1 pro manažery a hodnotu 2 pro zaměstnance. Sloupec typ je sloupec diskriminátor. V tomto scénáři můžete vytvořit podtřídu zaměstnanců a naplnit třídu pouze záznamy, které mají hodnotu typu 2.

 Při konfiguraci dědičnosti v třídách entit pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] přetáhněte jedinou tabulku, která obsahuje data dědičnosti, do návrháře dvakrát: jednou pro každou třídu v hierarchii dědičnosti. Po přidání tabulek do návrháře je připojte pomocí položky dědičnosti z panelu nástrojů **Návrhář relací objektů** a pak nastavte čtyři vlastnosti dědičnosti v okně **vlastnosti** .

## <a name="inheritance-properties"></a>Vlastnosti dědičnosti
 V následující tabulce jsou uvedeny vlastnosti dědičnosti a jejich popis:

|Vlastnost|Popis|
|--------------|-----------------|
|Vlastnost diskriminátoru|Vlastnost (namapovaná na sloupec), která určuje, do které třídy aktuální záznam patří.|
|Hodnota diskriminátoru základní třídy|Hodnota (ve sloupci určeném jako vlastnost diskriminátoru), která určuje, že záznam je základní třídou.|
|Hodnota diskriminátoru odvozené třídy|Hodnota (ve vlastnosti určené jako vlastnost diskriminátor), která určuje, že záznam je odvozenou třídou.|
|Výchozí dědičnost|Třída, která by měla být naplněna, pokud hodnota ve vlastnosti určené jako **vlastnost diskriminátoru** neodpovídá **hodnotě diskriminátoru základní třídy** ani **hodnoty diskriminátoru odvozené třídy**.|

 Vytvoření objektového modelu, který používá dědičnost a odpovídá relačním datům, může být poněkud matoucí. V tomto tématu najdete informace o základních konceptech a jednotlivých vlastnostech, které jsou potřeba ke konfiguraci dědičnosti. V následujících tématech najdete srozumitelnější vysvětlení způsobu konfigurace dědičnosti pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

|Téma|Popis|
|-----------|-----------------|
|[Postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Popisuje, jak konfigurovat třídy entit, které používají dědičnost s jednou tabulkou, pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|
|[Návod: Vytvoření tříd LINQ to SQL pomocí dědičnosti jedné tabulky (Návrhář relací objektů)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Poskytuje podrobné pokyny ke konfiguraci tříd entit, které používají dědičnost s jednou tabulkou, pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– návod: vytvoření LINQ to SQLch tříd (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (o/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [Začínáme](https://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

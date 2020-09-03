---
title: Objekty, které přidáváte do návrháře, používají jiné datové připojení než Návrhář aktuálně používá | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672293"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Objekty, které přidáváte do návrháře, obsahují jiné datové připojení než připojení momentálně používané návrhářem.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Objekty, které přidáváte do návrháře, používají jiné datové připojení než Návrhář aktuálně používá. Chcete nahradit připojení používané návrhářem?

 Při přidávání položek do [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) všechny položky používají jedno sdílené datové připojení. (Návrhová plocha představuje <xref:System.Data.Linq.DataContext> , který používá jedno připojení pro všechny objekty na povrchu.) Pokud přidáte objekt do návrháře, který používá datové připojení, které se liší od datového připojení, které je aktuálně používáno návrhářem, zobrazí se tato zpráva. Tuto chybu můžete vyřešit tak, že se rozhodnete zachovat stávající připojení. Pokud uděláte tuto volbu, vybraný objekt se nepřidá. Alternativně můžete zvolit přidání objektu a resetování <xref:System.Data.Linq.DataContext> připojení k novému připojení.

> [!NOTE]
> Kliknete-li na tlačítko **Ano**, všechny třídy entit na objektu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jsou namapovány na nové připojení.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Nahrazení stávajícího připojení pomocí připojení používaného vybraným objektem

- Klikněte na **Ano**.

     Vybraný objekt je přidán do objektu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a DataContext. připojení je nastaveno na nové připojení.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Chcete-li nadále používat existující připojení a zrušit přidávání vybraného objektu

- Klikněte na tlačítko **ne**.

     Akce se zrušila. Kontext DataContext. připojení zůstává nastaveno na existující připojení.

## <a name="see-also"></a>Viz také
 [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
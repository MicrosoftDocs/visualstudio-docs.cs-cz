---
title: Přehled použití místních souborů databáze v řešeních pro systém Office
description: Přečtěte si, jak můžete do svého řešení Office zahrnout databázový soubor, jako je například soubor SQL Server Express (. mdf) nebo soubor systém Microsoft Office Access (. mdb).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1a3166a88080eaee1042187c171c4938d236058a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526558"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Přehled použití místních souborů databáze v řešeních pro systém Office
  Do svého řešení Office můžete zahrnout soubor databáze, jako je například soubor SQL Server Express (*. mdf*) nebo soubor systém Microsoft Office Access (*. mdb*). To umožňuje koncovým uživatelům udržovat místní databázi v situacích, kdy není nutné spravovat centralizovanou databázi, například v řešení místního inventáře, které se používá pouze v jednom počítači.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Import databázového souboru do projektu
 Chcete-li importovat databázový soubor do projektu, použijte **Průvodce konfigurací zdroje dat** k vytvoření zdroje dat založeného na souboru databáze. Průvodce přidá do projektu soubor databáze a typovou datovou sadu.

## <a name="deploy-the-database-file"></a>Nasazení databázového souboru
 **Průvodce konfigurací zdroje dat** používá relativní cestu k vytvoření připojení k místnímu databázovému souboru. To vám umožní zkopírovat řešení z jednoho počítače do druhého, pokud udržujete relativní umístění souborů.

 Pokud vaše řešení nasadíte na server a pak ho rozšíříte na každého koncového uživatele, musíte ručně distribuovat databázový soubor a nainstalovat ho do stejné pozice relativně k dokumentu. To znamená, že koncový uživatel nemůže přesunout dokument do nového umístění na svém počítači, pokud mu také nepřesunul soubor databáze.

## <a name="local-database-files-and-caching-the-dataset"></a>Místní soubory databáze a datová sada pro ukládání do mezipaměti
 V řešeních na úrovni dokumentu pro systém Microsoft Office Excel a systém Microsoft Office Word můžete ukládat datové sady v dokumentu do mezipaměti tím, že označíte instanci datové sady atributem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Když do projektu přidáte soubor databáze pomocí **Průvodce konfigurací zdroje dat**, je do projektu automaticky přidána typová datová sada. Pro <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> tuto datovou sadu je zřídka nutné použít, protože data jsou v počítači uživatele již místní. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Data mezipaměti](../vsto/caching-data.md)

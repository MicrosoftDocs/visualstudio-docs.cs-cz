---
title: Visual Studio Data Tools for .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670104"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools for .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio a .NET Framework společně poskytují rozsáhlou podporu rozhraní API a nástrojů pro připojení k databázím, modelování dat v paměti a zobrazování dat v uživatelském rozhraní.  .NET Framework třídy, které poskytují funkce pro přístup k datům, se označují jako [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET společně s datovými nástroji v aplikaci Visual Studio byly původně navržené primárně pro podporu relačních databází a XML. Tyto dny, mnoho dodavatelů databáze NoSQL nebo třetích stran, nabízejí poskytovatele ADO.NET.

 Visual Studio 2015 Update 2 obsahuje nejnovější aktualizace            [nástrojů SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), které umožňují podporu pro nejnovější funkce v Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) a [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) podporuje ADO.NET, s výjimkou datových sad a souvisejících typů. Pokud cílíte na .NET Core a požadujete vrstvu mapování objektů (ORM), použijte [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 Následující diagram znázorňuje zjednodušený pohled na základní architekturu:

 ![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagram architektury raddata ADO.NET")

 Typický pracovní postup je následující:

1. Nainstalujte do místního počítače vývojovou nebo testovací databázi. Viz [instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md). Pokud používáte datovou službu Azure, tento krok není nezbytný.

2. Otestujte připojení k databázi (nebo ke službě nebo místnímu souboru) v aplikaci Visual Studio. Viz [přidat nová připojení](../data-tools/add-new-connections.md).

3. Volitelné Pomocí nástrojů vygenerujte a nakonfigurujte nový model. Modely založené na Entity Framework jsou výchozí doporučení pro nové aplikace. Model, podle toho, který používáte, je zdrojem dat, se kterým aplikace komunikuje. Model je logicky umístěný mezi databází nebo službou a aplikací.  Viz [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md).

4. Přetáhněte zdroj dat z okna **zdroje dat** na návrhovou plochu model Windows Forms, ASP.NET nebo Windows Presentation Foundation, abyste vygenerovali kód datové vazby, který zobrazí data uživateli způsobem, který určíte. Viz [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Přidejte vlastní kód pro věci, jako jsou obchodní pravidla, vyhledávání a ověřování dat, nebo můžete využít vlastní funkce, které podkladová databáze zpřístupňuje.

   Můžete přeskočit krok 3 a programovat aplikaci .NET a vydávat příkazy přímo do databáze namísto použití modelu. V takovém případě najdete příslušnou dokumentaci: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Všimněte si, že stále můžete použít Průvodce konfigurací zdroje dat a návrháře k vygenerování kódu datové vazby, když naplníte vlastní objekty v paměti a pak ovládací prvky uživatelského rozhraní pro vázání dat na tyto objekty.

## <a name="in-this-section"></a>V této části

- [Vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Přidání nových připojení](../data-tools/add-new-connections.md)

- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)

- [Nástroje modelu EDM (Entity Data Model) v sadě Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Další prostředky pro odstraňování chyb přístupu k datům](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Vytváření a správa databází a aplikací datové vrstvy v sadě Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Další prostředky pro odstraňování chyb přístupu k datům](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Viz také
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

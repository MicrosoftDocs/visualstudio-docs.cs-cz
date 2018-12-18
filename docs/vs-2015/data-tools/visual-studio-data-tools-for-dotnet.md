---
title: Visual Studio data tools pro rozhraní .NET | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 841311af90ddf4bedfb9d055e5764068cdc71632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859704"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools for .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio a rozhraní .NET Framework společně poskytují rozsáhlé rozhraní API a podpora nástrojů pro připojení k databázím, modelování dat v paměti a zobrazení dat v uživatelském rozhraní.  Tříd rozhraní .NET Framework, které poskytují přístup k datům funkce jsou označovány jako [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, spolu s daty nástroje v sadě Visual Studio byla původně určena především pro podporu relačních databází a XML. V dnešních dnech mnoho dodavatelů databáze typu NoSQL nebo třetími stranami, nabízejí poskytovatele ADO.NET.  
  
 Visual Studio 2015 Update 2 zahrnuje nejnovější aktualizace [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), které zajišťují podporu pro nejnovější funkce v Azure [SQL Database](https://azure.microsoft.com/en-us/services/sql-database/) a [SQL serveru 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore) podporuje technologie ADO.NET, s výjimkou datové sady a souvisejících typů. Pokud se zaměřujete na .NET Core a vyžadují vrstvu objektově relační mapování (ORM), použijte [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Následující diagram znázorňuje zjednodušenou zobrazení základní architektury:  
  
 ![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata Diagram architektury ADO.NET")  
  
 Typický pracovní postup je následující:  
  
1. Nainstalujte vývojové nebo testovací databáze na místním počítači. Zobrazit [instalace systémů databází, nástroje a ukázky](../data-tools/installing-database-systems-tools-and-samples.md). Pokud používáte službu Azure data, tento krok není nezbytný.  
  
2. Otestujte připojení k databázi (nebo službu nebo místní soubor) v sadě Visual Studio. Zobrazit [přidat nové připojení](../data-tools/add-new-connections.md).  
  
3. (Volitelné) Pomocí nástrojů vygenerovat a nakonfigurovat nový model. Modely založené na rozhraní Entity Framework jsou výchozí doporučení pro nové aplikace. Model, kteréhokoli z nich použijete, je zdroj dat, který aplikace komunikuje s. Model je logicky mezi databází nebo služby a aplikace.  Zobrazit [přidat nové zdroje dat](../data-tools/add-new-data-sources.md).  
  
4. Přetáhnout zdroje dat z **zdroje dat** okno na návrhovou plochu Windows Forms, ASP.NET nebo Windows Presentation Foundation ke generování kódu vázání dat, která tato data budou zobrazovat uživateli způsobem, který zadáte. Zobrazit [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Přidání vlastního kódu pro takové věci, jako jsou obchodní pravidla, vyhledávání a ověřování dat nebo využívat vlastní funkce, které zpřístupňuje základní databáze.  
  
   Můžete přeskočit krok 3 a programu .NET aplikace vydat příkazy přímo do databáze, nikoli pomocí modelu. V takovém případě najdou relevantní dokumentaci: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Všimněte si, že jste stále můžete použít Průvodce konfigurací zdroje dat a návrhářů pro generování kódu datové vazby při naplňování vlastních objektů v paměti a potom vytvořte datovou vazbu ovládacích prvků uživatelského rozhraní na tyto objekty.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Přidání nových připojení](../data-tools/add-new-connections.md)  
  
-   [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)  
  
-   [Nástroje modelu EDM (Entity Data Model) v sadě Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Další prostředky pro odstraňování chyb přístupu k datům](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Vytváření a správa databází a aplikací datové vrstvy v sadě Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Další prostředky pro odstraňování chyb přístupu k datům](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)








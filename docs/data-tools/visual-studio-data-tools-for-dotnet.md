---
title: Data Tools for .NET
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 67cf4969a5db8900910b375d4cf560b1e30da4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281068"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools for .NET

Visual Studio a .NET společně poskytují rozsáhlou podporu rozhraní API a nástrojů pro připojení k databázím, modelování dat v paměti a zobrazování dat v uživatelském rozhraní. Třídy .NET, které poskytují funkce pro přístup k datům, se označují jako [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET společně s nástroji pro data v aplikaci Visual Studio byla navržena primárně pro podporu relačních databází a XML. Tyto dny, mnoho dodavatelů databáze NoSQL nebo třetích stran, nabízejí poskytovatele ADO.NET.

[.NET Core](/dotnet/core/) podporuje ADO.NET, s výjimkou datových sad a jejich souvisejících typů. Pokud cílíte na .NET Core a potřebujete vrstvu pro mapování objektů (ORM), použijte [Entity Framework Core](/ef/core/).

Následující diagram znázorňuje zjednodušený pohled na základní architekturu:

![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typický pracovní postup

Typický pracovní postup je následující:

1. Nainstalujte do místního počítače vývojovou nebo testovací databázi. Viz [instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md). Pokud používáte datovou službu Azure, tento krok není nezbytný.

2. Otestujte připojení k databázi (nebo ke službě nebo místnímu souboru) v aplikaci Visual Studio. Viz [přidat nová připojení](../data-tools/add-new-connections.md).

3. Volitelné Pomocí nástrojů vygenerujte a nakonfigurujte nový model. Modely založené na Entity Framework jsou výchozí doporučení pro nové aplikace. Model, podle toho, který použijete, je zdrojem dat, se kterým aplikace komunikuje. Model je logicky umístěný mezi databází nebo službou a aplikací. Viz [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md).

4. Přetáhněte zdroj dat z okna **zdroje dat** na návrhovou plochu model Windows Forms, ASP.NET nebo Windows Presentation Foundation, abyste vygenerovali kód datové vazby, který zobrazí data uživateli způsobem, který určíte. Viz [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Přidejte vlastní kód pro věci, jako jsou obchodní pravidla, vyhledávání a ověřování dat, nebo můžete využít vlastní funkce, které podkladová databáze zpřístupňuje.

Můžete přeskočit krok 3 a programovat aplikaci .NET a vydávat příkazy přímo do databáze namísto použití modelu. V takovém případě najdete příslušnou dokumentaci: [ADO.NET](/dotnet/framework/data/adonet/index). Všimněte si, že stále můžete použít **Průvodce konfigurací zdroje dat** a návrháře k vygenerování kódu datové vazby, když naplníte vlastní objekty v paměti a pak ovládací prvky uživatelského rozhraní pro vázání dat na tyto objekty.

## <a name="see-also"></a>Viz také

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

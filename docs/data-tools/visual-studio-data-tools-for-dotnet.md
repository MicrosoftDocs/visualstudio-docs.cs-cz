---
title: Datové nástroje pro .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 1dcd8c256259baeef36939e19ce785e5efe7c80b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586039"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools for .NET

Visual Studio a .NET společně poskytují rozsáhlou podporu rozhraní API a nástrojů pro připojení k databázím, modelování dat v paměti a zobrazování dat v uživatelském rozhraní. Třídy .NET, které poskytují funkce pro přístup k datům, se označují jako [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, spolu s daty nástroje v sadě Visual Studio, je navržená především pro podporu relačních databází a XML. V dnešních dnech mnoho dodavatelů databáze typu NoSQL nebo třetími stranami, nabízejí poskytovatele ADO.NET.

[.NET Core](/dotnet/core/) podporuje ADO.NET, s výjimkou datových sad a jejich souvisejících typů. Pokud cílíte na .NET Core a potřebujete vrstvu pro mapování objektů (ORM), použijte [Entity Framework Core](/ef/core/).

Následující diagram znázorňuje zjednodušenou zobrazení základní architektury:

![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typický pracovní postup

Typický pracovní postup je následující:

1. Nainstalujte vývojové nebo testovací databáze na místním počítači. Zobrazit [instalace systémů databází, nástroje a ukázky](../data-tools/installing-database-systems-tools-and-samples.md). Pokud používáte službu Azure data, tento krok není nezbytný.

2. Otestujte připojení k databázi (nebo službu nebo místní soubor) v sadě Visual Studio. Zobrazit [přidat nové připojení](../data-tools/add-new-connections.md).

3. (Volitelné) Pomocí nástrojů vygenerovat a nakonfigurovat nový model. Modely založené na rozhraní Entity Framework jsou výchozí doporučení pro nové aplikace. Model, kteréhokoli z nich použijete, je zdroj dat, pomocí kterého aplikace komunikuje. Model je logicky mezi databází nebo služby a aplikace. Zobrazit [přidat nové zdroje dat](../data-tools/add-new-data-sources.md).

4. Přetáhnout zdroje dat z **zdroje dat** okno na návrhovou plochu Windows Forms, ASP.NET nebo Windows Presentation Foundation ke generování kódu vázání dat, která tato data budou zobrazovat uživateli způsobem, který zadáte. Zobrazit [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Přidání vlastního kódu pro takové věci, jako jsou obchodní pravidla, vyhledávání a ověřování dat nebo využívat vlastní funkce, které zpřístupňuje základní databáze.

Můžete přeskočit krok 3 a programu .NET aplikace vydat příkazy přímo do databáze, nikoli pomocí modelu. V takovém případě najdou relevantní dokumentaci: [ADO.NET](/dotnet/framework/data/adonet/index). Všimněte si, že se můžete stále použít **Průvodce konfigurací zdroje dat** , návrháři, generovat datové vazby kód při naplňování vlastních objektů v paměti a potom vytvořte datovou vazbu ovládacích prvků uživatelského rozhraní na tyto objekty.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

---
title: Vybrali jste databázový objekt od nepodporovaného poskytovatele databáze.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b1dd14c428b90b87e665aa41681b5a9e68eb00e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648011"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vybrali jste databázový objekt od nepodporovaného poskytovatele databáze.

**Návrhář o/R** podporuje pouze .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>). I když můžete kliknout na **OK** a pokračovat v práci s objekty z nepodporovaných zprostředkovatelů databází, může při spuštění docházet k neočekávanému chování.

> [!NOTE]
> Podporují se jenom datová připojení, která používají Zprostředkovatel dat .NET Framework pro SQL Server.

## <a name="options"></a>Možnosti

- Kliknutím na tlačítko **OK** pokračujte v navrhování tříd entit, které jsou mapovány na připojení, které používá nepodporovaného poskytovatele databáze. Pokud používáte nepodporované poskytovatele databází, může docházet k neočekávanému chování.

- Akci zastavíte kliknutím na tlačítko **Storno** . Vytvořte nebo použijte jiné datové připojení, které používá poskytovatele .NET Framework pro SQL Server.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
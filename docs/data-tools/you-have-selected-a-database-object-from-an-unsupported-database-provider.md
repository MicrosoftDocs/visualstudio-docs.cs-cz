---
title: Vybrali jste databázový objekt od nepodporovaného poskytovatele databáze.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5721cf340a09c138521e7134a0d19484561eb3a0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280977"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vybrali jste databázový objekt od nepodporovaného poskytovatele databáze.

**Návrhář o/R** podporuje pouze .NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient> ). I když můžete kliknout na **OK** a pokračovat v práci s objekty z nepodporovaných zprostředkovatelů databází, může při spuštění docházet k neočekávanému chování.

> [!NOTE]
> Podporují se jenom datová připojení, která používají Zprostředkovatel dat .NET Framework pro SQL Server.

## <a name="options"></a>Možnosti

- Kliknutím na tlačítko **OK** pokračujte v navrhování tříd entit, které jsou mapovány na připojení, které používá nepodporovaného poskytovatele databáze. Pokud používáte nepodporované poskytovatele databází, může docházet k neočekávanému chování.

- Akci zastavíte kliknutím na tlačítko **Storno** . Vytvořte nebo použijte jiné datové připojení, které používá poskytovatele .NET Framework pro SQL Server.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

---
title: 'Testovací oblast 6: Odstranit | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704514"
---
# <a name="test-area-6-delete"></a>Testovací oblast 6: Odstranění
Tato testovací oblast modulu plug-in pro řízení zdrojového kódu pokrývá akce odstranění.

 Ovládací prvek zdroje reaguje na akce odstranění v **Průzkumníku řešení**.

 Následuje seznam položek, které lze odstranit:

- Soubory

- Složky

- Project

  V závislosti na typu projektu můžete mít možnost **odebrat** projekt (ponechá soubory na disku) nebo **Odstranit** projekt (odebere soubory na disku). Buď akce odebere projekt nebo položku z **Průzkumníka řešení**.

## <a name="expected-behavior"></a>Očekávané chování
 Očekávané chování pro testovací případy v oblasti odstranění testu je:

- Odstraněná položka již není viditelná v **Průzkumníku řešení**.

- Nadřazený odstraněný projekt nebo položku je rezervován podle potřeby (případně s výzvou.)

- Po odstranění rezervováné nebo přidané položky se nezobrazí v okně **Čekající vrácení se změnami.**

- Položka stále existuje v úložišti správy zdrojového kódu, i po odstranění a musí být ručně vymazány.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Odstranění klientského projektu|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vyjměte celý projekt z řešení|Společné očekávané chování.|
|Odstranění prázdného souboru|1. Vytvořte klientský projekt.<br />2. Přidejte do projektu soubor s nulovým bajtem.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Vyberte soubor, odstraňte jej.|Společné očekávané chování.|
|Odstranění složky s jedním souborem|1. Vytvořte řešení jednoho projektu.<br />2. Přidejte složku.<br />3. Přidejte jeden soubor do složky.<br />4. Přidejte řešení do správy zdrojového kódu.<br />5. Podívejte se na projekt, abyste se vyhnuli výzvám.<br />6. Odstraňte složku.|Společné očekávané chování.|
|Odstranění webového projektu systému souborů|1. Vytvořte webový projekt systému souborů (pomocí tlačítka Procházet určete cestu UNC).<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Odstraňte celý projekt z řešení.<br />4. Opakujte kroky 1 až 3 pro místní webový projekt (cvičení různých cest prostřednictvím kódu, ale má stejné externí rozhraní a chování).|Společné očekávané chování.|
|Odstranění souboru z webového projektu systému souborů|1. Vytvořte webový projekt systému souborů.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Odstraňte soubor z projektu.<br />4. Opakujte kroky 1 až 3 pro místní webový projekt (cvičení různých cest prostřednictvím kódu, ale má stejné externí rozhraní a chování).|Společné očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

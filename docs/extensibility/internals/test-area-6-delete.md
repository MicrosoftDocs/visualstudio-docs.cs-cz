---
title: 'Testovací oblast 6: odstranit | Microsoft Docs'
description: Tato testovací oblast zdrojového kódu pokrývá akce odstranění v Průzkumník řešení pro modul plug-in správy zdrojových kódů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1371472a4dec265b5e476d96a32cb725e91ce7fe
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487553"
---
# <a name="test-area-6-delete"></a>Testovací oblast 6: Odstranit
Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá akce odstranění.

 Správa zdrojového kódu reaguje na akce odstranění v **Průzkumník řešení**.

 Následuje seznam položek, které je možné odstranit:

- Soubory

- Složky

- Project

  V závislosti na typu projektu může být k dispozici možnost **Odebrat** projekt (nechat soubory na disku) nebo **Odstranit** projekt (soubory budou odstraněny na disku). Buď akce odebere projekt nebo položku z **Průzkumník řešení**.

## <a name="expected-behavior"></a>Očekávané chování
 Očekávané chování pro testovací případy v oblasti odstranění testu je:

- Odstraněná položka již není viditelná v **Průzkumník řešení**.

- Nadřazená položka odstraněného projektu nebo položky je rezervována podle potřeby (případně s výzvou.)

- Po odstranění rezervované nebo přidané položky se tato položka nezobrazí v okně **nedokončené vrácení se změnami** .

- Položka stále existuje v úložišti správy zdrojů, i po odstranění, a je nutné ji ručně vyprázdnit.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Odstranění klientského projektu|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. odeberte celý projekt z řešení.|Obvyklé očekávané chování.|
|Odstranit prázdný soubor|1. Vytvořte projekt klienta.<br />2. Přidejte do projektu soubor s nulovým bajtem.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Vyberte soubor a odstraňte ho.|Obvyklé očekávané chování.|
|Odstraní složku s jedním souborem.|1. Vytvořte jedno řešení projektu.<br />2. přidejte složku.<br />3. Přidejte do složky jeden soubor.<br />4. Přidejte řešení do správy zdrojového kódu.<br />5. Prohlédněte si projekt, abyste se vyhnuli zobrazování výzev.<br />6. Odstraňte složku.|Obvyklé očekávané chování.|
|Odstranit webový projekt systému souborů|1. Vytvořte webový projekt systému souborů (pomocí tlačítka Procházet zadejte cestu UNC).<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. odeberte celý projekt z řešení.<br />4. Opakujte kroky 1 až 3 pro místní webový projekt (cvičení různých cest prostřednictvím kódu, ale má stejné externí rozhraní a chování).|Obvyklé očekávané chování.|
|Odstranění souboru z webového projektu systému souborů|1. Vytvořte webový projekt systému souborů.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Odstraňte soubor z projektu.<br />4. Opakujte kroky 1 až 3 pro místní webový projekt (cvičení různých cest prostřednictvím kódu, ale má stejné externí rozhraní a chování).|Obvyklé očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

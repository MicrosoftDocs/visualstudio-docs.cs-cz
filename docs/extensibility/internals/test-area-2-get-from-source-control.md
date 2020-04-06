---
title: 'Testovací oblast 2: Získat ze správy zdrojového kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704602"
---
# <a name="test-area-2-get-from-source-control"></a>Testovací oblast 2: Načtení ze správy zdrojového kódu
Tato testovací oblast zahrnuje testovací případy pro načítání položek z úložiště verzí pomocí příkazu Get. Tyto testovací případy lze použít pro místní i webové projekty.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech.

##### <a name="get-latest-version"></a>Získejte nejnovější verzi:

- **Soubor**, **Správa zdrojového kódu**, **Získat nejnovější verzi**.

- **Soubor**, **získat nejnovější verzi**.

- Místní **nabídka, Získat nejnovější verzi**.

- Získat: **Soubor**, **Řízení zdrojového kódu**, **Získat**.

## <a name="expected-behavior"></a>Očekávané chování

##### <a name="get-latest-version"></a>Získejte nejnovější verzi:
 Provede tiché (žádné ui) načítání nejnovější verze položky z úložiště verzí.

##### <a name="get"></a>Dostat:
 Zobrazí dialogové okno **Získat** a umožní uživateli provádět změny sady souborů, která bude načtena, a také upravit možnosti, které ovlivňují způsob načítání souborů.

## <a name="test-cases"></a>Testovací případy

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Získat nejnovější verzi souboru, který neexistuje místně|1. Vytvořte projekt.<br />2. Přidejte položku do projektu.<br />3. Vložte projekt pod sohledem zdroje.<br />4. Odstraňte místní kopii položky.<br />5. Získejte nejnovější verzi položky (Místní nabídka, **Získat nejnovější verzi).**|Soubor položky je načten místně.|
|Získat soubor, který neexistuje místně|1. Vytvořte projekt.<br />2. Přidejte položku do projektu.<br />3. Vložte projekt pod sohledem zdroje.<br />4. Odstraňte místní kopii položky.<br />5. Získejte položku **(Soubor,** **Řízení zdrojového kódu**, **Získat** \<položku>).|Soubor položky je načten místně.|
|Získejte soubor, který byl rezervován výhradně a upraven místně|1. Vytvořte projekt.<br />2. Přidejte položku do projektu.<br />3. Vložte projekt pod sohledem zdroje.<br />4. Podívejte se na položku projektu výhradně.<br />5. Upravte místní kopii.<br />6. Získejte nejnovější verzi položky **(Soubor**, **Získejte nejnovější verzi položky** \<>). Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />7. V dialogovém okně upozornění klepněte na tlačítko **Nahradit.**|**ReResult z kroku 6**`:`<br /><br /> Dialogové okno Upozornění označuje, že soubor je rezervován.<br /><br /> **ReResult z kroku 7:**<br /><br /> Změněný místní soubor je nahrazen původní verzí z úložiště verzí.<br /><br /> Soubor je čtení/zápis.|
|Získat a nahradit soubor, který je rezervován, sdílen a upraven místně|1. Vytvořte nový projekt.<br />2. Přidejte položku do projektu.<br />3. Vložte projekt pod sohledem zdroje.<br />4. Podívejte se na položku projektu jako sdílenou.<br />5. Upravte místní kopii.<br />6. Získejte nejnovější verzi položky **(Soubor**, **Získejte nejnovější verzi položky** \<>). Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />7. V dialogovém okně upozornění klepněte na **tlačítko Nahradit.**|**Výsledek kroku 6:**<br /><br /> Dialogové okno Upozornění označuje, že soubor je rezervován.<br /><br /> **Výsledek kroku 7:**<br /><br /> Změněný místní soubor je nahrazen původní verzí z úložiště verzí.<br /><br /> Soubor je čtení/zápis.|
|Získejte soubor, který existuje místně, stejně jako nejnovější verze v úložišti verzí|1. Vytvořte nový projekt.<br />2. Přidejte položku do projektu.<br />3. Vložte projekt pod sohledem zdroje.<br />4. Získejte položku **(Soubor,** **Řízení zdrojového kódu**, **Získat** \<položku>).|Místní soubor se nezmění.|
|Získejte řešení s jedním projektem|1. Vytvořte řešení s jedním projektem.<br />2. Umístěte roztok pod spouštění zdrojů.<br />3. Odstraňte všechny soubory projektu místně.<br />4. Získejte řešení **(Soubor,** **Zdrojové zdroje**, **Get).**|Všechny smazané soubory jsou obnoveny místně.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

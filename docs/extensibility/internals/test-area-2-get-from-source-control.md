---
title: 'Testovací oblast 2: získat ze správy zdrojového kódu | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704602"
---
# <a name="test-area-2-get-from-source-control"></a>Testovací oblast 2: Získání ze správy zdrojového kódu
Tato testovací oblast pokrývá testovací případy pro načítání položek z úložiště verzí pomocí příkazu Get. Tyto testovací případy lze použít pro místní i pro webové projekty.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí.

##### <a name="get-latest-version"></a>Získat nejnovější verzi:

- **Soubor**, Správa **zdrojového kódu**, **získat nejnovější verzi**.

- **Soubor**, **získat nejnovější verzi**.

- Místní nabídka – **získat nejnovější verzi**

- Get: **File**, **Source Control**, **Get**.

## <a name="expected-behavior"></a>Očekávané chování

##### <a name="get-latest-version"></a>Získat nejnovější verzi:
 Provede tiché načtení nejnovější verze položky z verze Store (bez uživatelského rozhraní).

##### <a name="get"></a>Čtěte
 Zobrazí dialogové okno **získat** , ve kterém může uživatel provést změny v sadě souborů, která bude načtena, a změnit možnosti, které mají vliv na to, jak jsou soubory načteny.

## <a name="test-cases"></a>Testovací případy

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Získat nejnovější verzi souboru, který neexistuje v místním prostředí|1. Vytvořte projekt.<br />2. přidejte položku do projektu.<br />3. Umístěte projekt pod správu zdrojového kódu.<br />4. Odstraňte místní kopii položky.<br />5. načíst nejnovější verzi položky (místní nabídka, **získat nejnovější verzi**)|Soubor položky se načte lokálně.|
|Získat soubor, který neexistuje místně|1. Vytvořte projekt.<br />2. přidejte položku do projektu.<br />3. Umístěte projekt pod správu zdrojového kódu.<br />4. Odstraňte místní kopii položky.<br />5. Získejte položku (**soubor**, Správa **zdrojového kódu**, **získat** \<item> ).|Soubor položky se načte lokálně.|
|Získat soubor, který byl registrován exkluzivně a lokálně pozměněn|1. Vytvořte projekt.<br />2. přidejte položku do projektu.<br />3. Umístěte projekt pod správu zdrojového kódu.<br />4. Prohlédněte si výhradně položku projektu.<br />5. Upravte místní kopii.<br />6. Získejte nejnovější verzi položky (**soubor**, **načíst nejnovější verzi** \<item> ). V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />7. v dialogovém okně upozornění klikněte na tlačítko **nahradit** .|**Výsledek z kroku 6**`:`<br /><br /> Dialogové okno upozornění označuje, že je soubor rezervován.<br /><br /> **Výsledek z kroku 7:**<br /><br /> Změněný místní soubor je nahrazen původní verzí z úložiště verzí.<br /><br /> Soubor je pro čtení i zápis.|
|Získat a nahradit soubor, který je rezervován, sdílen a upravován místně|1. Vytvořte nový projekt.<br />2. přidejte položku do projektu.<br />3. Umístěte projekt pod správu zdrojového kódu.<br />4. Prohlédněte si položku projektu jako sdílenou.<br />5. Upravte místní kopii.<br />6. Získejte nejnovější verzi položky (**soubor**, **načíst nejnovější verzi** \<item> ). V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />7. v dialogovém okně upozornění klikněte na **nahradit** .|**Výsledek z kroku 6:**<br /><br /> Dialogové okno upozornění označuje, že je soubor rezervován.<br /><br /> **Výsledek z kroku 7:**<br /><br /> Změněný místní soubor je nahrazen původní verzí z úložiště verzí.<br /><br /> Soubor je pro čtení i zápis.|
|Získat soubor, který existuje místně, stejný jako nejnovější verze v úložišti verzí|1. Vytvořte nový projekt.<br />2. přidejte položku do projektu.<br />3. Umístěte projekt pod správu zdrojového kódu.<br />4. Získejte položku (**soubor**, Správa **zdrojového kódu**, **získat** \<item> ).|Místní soubor je nezměněný.|
|Získání řešení pomocí jednoho projektu|1. Vytvořte řešení pomocí jednoho projektu.<br />2. Umístěte řešení do správy zdrojového kódu.<br />3. Odstraňte všechny soubory projektu místně.<br />4. Získejte řešení (**soubor**, Správa **zdrojového kódu**, **získat**).|Všechny odstraněné soubory se obnoví místně.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

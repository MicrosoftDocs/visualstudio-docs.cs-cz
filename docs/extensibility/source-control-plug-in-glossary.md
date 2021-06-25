---
title: Glosář modulů plug-in správy zdrojového kódu | Microsoft Docs
description: Tento článek obsahuje užitečné termíny a definice, které se týkají dokumentace k sadě SDK modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05b215de4191362a539d3b03ac858da6bb7ee292
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899521"
---
# <a name="source-control-plug-in-glossary"></a>Glosář modulu plug-in zdrojového kódu
Následující užitečné termíny a definice se týkají dokumentace k sadě SDK modulu plug-in správy zdrojového kódu.

## <a name="definitions"></a>Definice
 Kontrola Když uživatel provede změny v pracovní kopii, musí uživatel odeslat změny z pracovní kopie do úložiště centrální správy zdrojového kódu. Tím se vytvoří nová revize souboru, která je k dispozici ostatním uživatelům. Tento proces se nazývá kontrola.

 Podívejte se na část Žádost o pracovní kopii z úložiště a informujte úložiště o svém záměru ho upravit. Pracovní kopie odráží stav projektu v okamžiku, kdy je rezervován.

 Klient: Program, který používá systém správy zdrojového kódu. Pro účely této dokumentace se jedná o integrované vývojové Visual Studio ideu.

 Komentář Zpráva popisující změny, které může uživatel připojit k revizi při provedení operace správy zdrojového kódu

 Konflikt Situace, kdy se dva uživatelé pokusí se změnami provést změny ve stejné oblasti stejného souboru. Obvykle je nutné provést sloučení.

 Adresář Místní složka na straně klienta se označuje jako adresář. Jedná se o kopii, ve které uživatel provádí změny. Existuje mnoho pracovních kopií daného projektu. obecně má každý vývojář svou vlastní kopii.

 Operace Get (Získat) přináší funkční kopii uživatele aktuální s kopií úložiště. Na rozdíl od rezervace se získání provede, když uživatel jednoduše potřebuje nejnovější kopii, ale hodlá provést žádné změny.

 Historie– obvykle se jedná o souhrn všech pokladny, kontrolních funkcí, aktualizací, značek a verzí provedených v úložišti správy zdrojového kódu.

 Integrované vývojové prostředí (IDE) obecně označuje Visual Studio integrované vývojové prostředí. Může ale také odkazovat na další klientská prostředí, která rozpoznává rozhraní API modulu plug-in správy zdrojového kódu.

 Sloučení: Proces, během kterého se zkombinují dva nebo více souborů zdrojového kódu, aby se zkombinuje nový soubor, který zahrnuje všechny funkce z předchozích souborů. Tento koncept je nezbytný pro řízení verzí, kdy dva nebo více vývojářů pracuje na souborech současně.

 Project (Projekt) Složka správy zdrojového kódu se často označuje jako projekt. Tento problém nemá žádný vztah s projekty nebo řešeními v Visual Studio.

 Modul plug-in Knihovna DLL, která poskytuje funkce správy zdrojového kódu implementací rozhraní API modulu plug-in správy zdrojového kódu.

 Repository (Úložiště) Hlavní kopie, do které systém správy zdrojového kódu ukládá úplnou historii revizí projektu. Každý projekt má přesně jedno úložiště.

 Revize Potvrzená změna v historii souboru nebo sady souborů Revize je jeden snímek v neustále se měnícím projektu.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

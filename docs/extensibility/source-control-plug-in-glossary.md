---
title: Glosář modulu plug-in pro řízení zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699913"
---
# <a name="source-control-plug-in-glossary"></a>Glosář modulu plug-in zdrojového kódu
Následující užitečné termíny a definice se vystydnou do dokumentace sady Plug-in s d-in správy zdrojového kódu.

## <a name="definitions"></a>Definice
 Vrácení se změnami: Pokud uživatel provede změny v pracovní kopii, musí odeslat změny z pracovní kopie do centrálního úložiště správy zdrojového kódu. Tím se vytvoří nová revize souboru, která je k dispozici ostatním uživatelům. Tento proces se nazývá vrácení se změnami.

 Pokladna Žádost o pracovní kopii z úložiště, informování úložiště o vašem záměru ji upravit. Pracovní kopie odráží stav projektu od okamžiku, kdy je rezervován.

 Klient Program, který používá systém správy zdrojového kódu. Pro účely této dokumentace je IDE sady Visual Studio.

 Komentář: Zpráva popisující změny, které může uživatel připojit k revizi při provádění operace správy zdrojového kódu.

 Konflikt Situace, kdy se dva uživatelé pokusí o vrácení změn ve stejné oblasti stejného souboru. Obvykle musí být provedeno sloučení.

 Adresář Místní složka na straně klienta se označuje jako adresář. Toto je kopie, ve které uživatel skutečně provede změny. Může existovat mnoho pracovních kopií daného projektu; obvykle má každý vývojář svou vlastní kopii.

 Get A get operace přináší uživatele pracovní kopie aktuální s kopií úložiště. Na rozdíl od pokladny se get provádí, když uživatel jednoduše potřebuje nejnovější kopii, ale má v úmyslu provést žádné změny.

 Historie Obvykle se jedná o souhrn všech pořazovacích šeků, vrácení se změnami, aktualizací, značek a verzí provedených v úložišti správy zdrojového kódu.

 IDE obecně odkazuje na integrované vývojové prostředí sady Visual Studio. Může však také odkazovat na jiná klientská prostředí, která rozpoznávají rozhraní api modulu plug-in správy zdrojového kódu.

 Sloučit Proces, během kterého jsou dva nebo více souborů zdrojového kódu kombinovány a tvoří nový soubor, který zahrnuje všechny funkce z předchozích souborů. Tento koncept je důležité v řízení verzí, kde dva nebo více vývojářů pracovat na soubory současně.

 Složka správy zdrojového kódu projektu A se často označuje jako projekt. To nemá žádný vztah s projekty nebo řešení v sadě Visual Studio.

 Modul DLL, která poskytuje funkce správy zdrojového kódu implementací rozhraní API modulu plug-in správy zdrojového kódu.

 Úložiště Hlavní kopie, kde systém správy zdrojového kódu ukládá úplnou historii revizí projektu. Každý projekt má přesně jedno úložiště.

 Revize Potvrzená změna v historii souboru nebo sady souborů. Revize je jeden snímek v neustále se měnícím projektu.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

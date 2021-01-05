---
title: Glosář modulu plug-in správy zdrojových kódů | Microsoft Docs
description: Tento článek obsahuje užitečné výrazy a definice, které se vztahují k dokumentaci k sadě SDK modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f5b878efd9d937f532526ed3b49ad41228749b47
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715402"
---
# <a name="source-control-plug-in-glossary"></a>Glosář modulu plug-in zdrojového kódu
Následující užitečné výrazy a definice se týkají dokumentace sady SDK modulu plug-in správy zdrojového kódu.

## <a name="definitions"></a>Definice
 Vrácení se změnami, když uživatel provede změny v pracovní kopii, musí odeslat změny z pracovní kopie do centrálního úložiště správy zdrojového kódu. Tím se vytvoří nová revize souboru, která je k dispozici ostatním uživatelům. Tento proces se nazývá vrácení se změnami.

 Zarezervujte Act o žádosti o pracovní kopii z úložiště, který informuje úložiště záměru o jeho úpravě. Pracovní kopie odráží stav projektu v době, kdy je rezervován.

 Klient aplikace, která používá systém správy zdrojového kódu. Pro účely této dokumentace je to integrované vývojové prostředí (IDE) sady Visual Studio.

 Komentář zprávy popisující změny, které se uživatel může připojit k revizi, když je provedena operace správy zdrojových kódů.

 Dojde ke konfliktu situace, když se dva uživatelé pokusí vrátit se změnami stejnou oblast stejného souboru. Sloučení je typicky nutné provést.

 Adresářovou místní složkou na straně klienta se říká adresář. Jedná se o kopii, ve které uživatel skutečně provádí změny. Může existovat mnoho pracovních kopií daného projektu; Obecně platí, že každý vývojář má svoji vlastní kopii.

 Operace Get přinese aktuální pracovní kopii uživatele do kopie úložiště. Na rozdíl od registrace se provede Get, když uživatel jednoduše potřebuje nejnovější kopii, ale zamýšlí dělat žádné změny.

 Historie je obvykle souhrn všech rezervací, vrácení se změnami, aktualizací, značek a vydání, které se provádí v úložišti správy zdrojového kódu.

 Rozhraní IDE obecně odkazuje na integrované vývojové prostředí sady Visual Studio. Může však také odkazovat na jiná klientská prostředí, která rozpoznávají rozhraní API modulu plug-in správy zdrojového kódu.

 Sloučení procesu, během kterého jsou dva nebo více souborů zdrojového kódu kombinovány, aby tvořily nový soubor, který zahrnuje všechny funkce z předchozích souborů. Tento koncept je nezbytný v řízení verze, kde dva nebo více vývojářů pracuje na souborech současně.

 Projekt složky správy zdrojového kódu se často označuje jako projekt. Nemá žádný vztah s projekty nebo řešeními v aplikaci Visual Studio.

 Modul plug-in knihovny DLL, která poskytuje funkce správy zdrojového kódu implementací rozhraní API modulu plug-in správy zdrojového kódu.

 Úložiště hlavní kopie, kde systém správy zdrojů ukládá úplnou historii revizí projektu. Každý projekt má přesně jedno úložiště.

 Revize potvrzené změny v historii souboru nebo sady souborů. Revize je jeden snímek s nepřetržitou změnou projektu.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

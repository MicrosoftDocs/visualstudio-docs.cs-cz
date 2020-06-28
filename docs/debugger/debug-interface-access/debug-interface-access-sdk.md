---
title: Debug Interface Access SDK | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da0ced56e8bf7e61e7fa5251e834a762d4c66650
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468691"
---
# <a name="debug-interface-access-sdk"></a>Přístup k rozhraní ladění SDK

Microsoft Debug Interface Access Software Development Kit (DIA SDK) poskytuje přístup k ladicím informacím uloženým v souborech databáze programu (PDB) generovaných nástroji Microsoft postcompiler Tools. Vzhledem k tomu, že formát souboru. pdb generovaný nástroji postcompiler přechází do stálé revize, je vystavení tohoto formátu nepraktické. Pomocí rozhraní DIA API můžete vyvíjet aplikace, které hledají a procházejí informace o ladění uložené v souboru. pdb. Takové aplikace můžou například sledovat informace o zpětném trasování zásobníku sestav a analyzovat data o výkonu.

## <a name="in-this-section"></a>V této části

[Začínáme](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Poskytuje přehled funkcí DIA SDK a určuje, kde je DIA SDK nainstalován, a také požadované soubory hlaviček a knihoven.

[Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Poskytuje pokyny, jak použít rozhraní API DIA k dotazování na soubor. pdb.

[Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Popisuje, jak se symboly a značky symbolů používají v rozhraní DIA API.

[Reference](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Obsahuje rozhraní, metody, výčty a struktury rozhraní DIA API.

[Dia2dump – ukázka](../../debugger/debug-interface-access/dia2dump-sample.md)

Ukazuje, jak používat rozhraní DIA API k hledání a procházení informací o ladění.

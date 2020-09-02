---
title: Debug Interface Access SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197624"
---
# <a name="debug-interface-access-sdk"></a>Přístup k rozhraní ladění SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Microsoft Debug Interface Access Software Development Kit (DIA SDK) poskytuje přístup k ladicím informacím uloženým v souborech databáze programu (PDB) generovaných nástroji Microsoft postcompiler Tools. Vzhledem k tomu, že formát souboru. pdb generovaný nástroji postcompiler přechází do stálé revize, je vystavení tohoto formátu nepraktické. Pomocí rozhraní DIA API můžete vyvíjet aplikace, které hledají a procházejí informace o ladění uložené v souboru. pdb. Takové aplikace můžou například sledovat informace o zpětném trasování zásobníku sestav a analyzovat data o výkonu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Poskytuje přehled funkcí DIA SDK a určuje, kde je DIA SDK nainstalován, a také požadované soubory hlaviček a knihoven.  
  
 [Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Poskytuje pokyny, jak použít rozhraní API DIA k dotazování na soubor. pdb.  
  
 [Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Popisuje, jak se symboly a značky symbolů používají v rozhraní DIA API.  
  
 [Odkaz](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Obsahuje rozhraní, metody, výčty a struktury rozhraní DIA API.  
  
 [Dia2dump – ukázka](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Ukazuje, jak používat rozhraní DIA API k hledání a procházení informací o ladění.  
  
 [Dia2dump.cpp – zdrojový soubor](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Zdrojový kód, který používá [Ukázka Dia2dump –](../../debugger/debug-interface-access/dia2dump-sample.md) k předvedení rozhraní DIA API.

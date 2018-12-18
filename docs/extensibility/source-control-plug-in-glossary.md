---
title: Zdroj ovládacího prvku modulu Plug-in Glosář | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ccfd4cbbbca86d3b6e93d9998410c5dea117328d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139023"
---
# <a name="source-control-plug-in-glossary"></a>Modul Plug-in Glosář zdroj ovládacího prvku
Následující užitečné termíny a definice se týkají dokumentace zdroj ovládacího prvku Plug-in SDK.  
  
## <a name="definitions"></a>Definice  
 Vrácení se změnami  
 Když uživatel provede změny pracovní kopie, musí uživatel odešle změny z je pracovní kopie do úložiště správy centrální zdrojů. Tím se vytvoří novou revizi souboru, který je k dispozici jiným uživatelům. Tento proces se nazývá vrátit se změnami.  
  
 Rezervovat  
 V rámci požadavku kopírování pracovní z úložiště, informuje o úložišti vašich představ, jak v hotové. Pracovní kopie odráží stav projektu od okamžiku, kdy je rezervována.  
  
 Klient  
 Program, který používá systém správy zdrojového kódu. Pro účely této dokumentace je Visual Studio IDE.  
  
 Komentář  
 Zpráva popisující změny, které uživatel může připojit k revizi při operaci správy zdrojů.  
  
 Konflikt  
 Stav, pokud dva uživatelé pokusí vrátit se změnami do stejné oblasti stejného souboru. Obvykle je nutné provést sloučení.  
  
 Adresář  
 Do místní složky klienta se označuje jako adresář. Toto je kopie, ve kterém uživatel ve skutečnosti provede změny. Může být mnoho pracovní kopie daného projektu. Každý vývojář má obvykle své aplikace.  
  
 GET  
 Operace získání přináší uživatele pracovní kopie aktuální s kopii úložiště. Na rozdíl od checkout se provádí get, když uživatel jednoduše vyžaduje nejnovější kopie, ale v úmyslu provést žádné změny.  
  
 Historie  
 Obvykle je souhrn všech rezervace, vrácení se změnami, aktualizace, značky a verzí v úložiště řízení zdrojů.  
  
 IDE – integrované vývojové prostředí  
 Obecně odkazuje na Visual Studio integrované vývojové prostředí. Však může také podívat na jiných prostředích klienta, které rozhraní API ovládacího prvku Plug-in Zdroj rozpoznat.  
  
 Sloučit  
 Proces během dvou nebo více zdroje spojení souborů kód k vytvoření nového souboru, která zahrnuje všechny funkce z předchozí soubory. Tento koncept je důležité ve správě verzí, kde dva nebo více vývojářů práci soubory současně.  
  
 Projekt  
 Zdrojové složky ovládací prvek se často označuje jako projekt. To nemá žádný vztah s řešeními nebo projekty v sadě Visual Studio.  
  
 modul plug-in  
 Knihovnu DLL, kterou poskytuje funkce správy zdrojového implementací rozhraní API ovládacího prvku Plug-in zdroje.  
  
 Úložiště  
 Hlavní kopii kde zdroj řízení systému ukládá historie revizí úplné projektu. Každý projekt má přesně jeden úložiště.  
  
 Revize  
 Potvrdit změny v historii souboru nebo sadu souborů. Revize je jedním snímku v nepřetržitě změna projektu.  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
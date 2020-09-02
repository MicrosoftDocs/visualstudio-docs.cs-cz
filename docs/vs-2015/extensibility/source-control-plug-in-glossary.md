---
title: Glosář modulu plug-in správy zdrojových kódů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160609"
---
# <a name="source-control-plug-in-glossary"></a>Glosář modulu plug-in zdrojového kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující užitečné výrazy a definice se týkají dokumentace sady SDK modulu plug-in správy zdrojového kódu.  
  
## <a name="definitions"></a>Definice  
 Vrátit  
 Když uživatel provede změny v pracovní kopii, musí odeslat změny z pracovní kopie do centrálního úložiště správy zdrojového kódu. Tím se vytvoří nová revize souboru, která je k dispozici ostatním uživatelům. Tento proces se nazývá vrácení se změnami.  
  
 Rezervovat  
 Způsob, jakým se žádá o pracovní kopii z úložiště, a to s popisem úložiště záměru pro jeho úpravu. Pracovní kopie odráží stav projektu v době, kdy je rezervován.  
  
 Klient  
 Program, který používá systém správy zdrojového kódu. Pro účely této dokumentace je to integrované vývojové prostředí (IDE) sady Visual Studio.  
  
 Komentář  
 Zpráva popisující změny, které může uživatel připojit k revizi, když je provedena operace správy zdrojových kódů.  
  
 Konflikt  
 Situace, kdy se dva uživatelé pokusí vrátit se změnami do stejné oblasti stejného souboru. Sloučení je typicky nutné provést.  
  
 Adresář  
 Místní složka na straně klienta se nazývá adresář. Jedná se o kopii, ve které uživatel skutečně provádí změny. Může existovat mnoho pracovních kopií daného projektu; Obecně platí, že každý vývojář má svoji vlastní kopii.  
  
 Získat  
 Operace Get přinese aktuální pracovní kopii uživatele do kopie úložiště. Na rozdíl od registrace se provede Get, když uživatel jednoduše potřebuje nejnovější kopii, ale zamýšlí dělat žádné změny.  
  
 Historie  
 Obvykle je souhrn všech rezervací, vrácení se změnami, aktualizací, značek a vydání v úložišti správy zdrojů.  
  
 IDE – integrované vývojové prostředí  
 Obecně odkazuje na integrované vývojové prostředí sady Visual Studio. Může však také odkazovat na jiná klientská prostředí, která rozpoznávají rozhraní API modulu plug-in správy zdrojového kódu.  
  
 Sloučit  
 Proces, během kterého jsou kombinovány dva nebo více souborů se zdrojovým kódem, aby bylo možné vytvořit nový soubor, který zahrnuje všechny funkce z předchozích souborů. Tento koncept je nezbytný v řízení verze, kde dva nebo více vývojářů pracuje na souborech současně.  
  
 Project  
 Složka správy zdrojového kódu se často označuje jako projekt. Nemá žádný vztah s projekty nebo řešeními v aplikaci Visual Studio.  
  
 Modul plug-in  
 Knihovna DLL, která poskytuje funkce správy zdrojového kódu implementací rozhraní API modulu plug-in správy zdrojového kódu.  
  
 Repository  
 Hlavní kopie, kde systém správy zdrojů ukládá úplnou historii revizí projektu. Každý projekt má přesně jedno úložiště.  
  
 Revize  
 Potvrzená změna v historii souboru nebo sady souborů. Revize je jeden snímek s nepřetržitou změnou projektu.  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

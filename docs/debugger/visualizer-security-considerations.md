---
title: Posouzení zabezpečení Vizualizér | Microsoft Docs
description: Vizualizér pro ladicí program sady Visual Studio musí běžet s úplným vztahem důvěryhodnosti. Při psaní můžete znát možné bezpečnostní hrozby a přijmout vhodná opatření.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db18a1443b0c4faaa288a887a22d935d243f678
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149739"
---
# <a name="visualizer-security-considerations"></a>Hlediska zabezpečení vizualizéru
Zápis Vizualizér zahrnuje možné bezpečnostní hrozby. Pro tyto potenciální hrozby aktuálně neexistuje žádný známý zneužitcí software, ale vývojáři je musí znát a přijmout vhodná bezpečnostní opatření, jak je popsáno zde, abyste se mohli chránit před neoprávněným zneužitím.

 Nástroje pro vizualizace ladicího programu vyžadují větší oprávnění, než povoluje aplikace s částečnou důvěryhodností. Když zastavíte kód s částečnou důvěryhodností, vizualizace se nenačte. Chcete-li provést ladění pomocí vizualizér, je nutné spustit kód s úplným vztahem důvěryhodnosti.

## <a name="possible-malicious-debuggee-component"></a>Možná škodlivá komponenta laděného procesu
 Vizualizace se skládají z aspoň dvou tříd: jeden na straně ladicího programu a druhý na laděného procesu straně. Vizualizace jsou často nasazeny v samostatných sestaveních, která jsou vložena do speciálních adresářů, ale mohou být také načtena z laděného procesu. Pokud k tomu dojde, ladicí program převezme kód z laděného procesu a spustí ho v ladicím programu s úplným vztahem důvěryhodnosti.

 Spuštění laděného procesu kódu s úplným vztahem důvěryhodnosti se bude problematické, pokud laděného procesu není plně důvěryhodný. Pokud se Vizualizér pokusí načíst částečně důvěryhodné sestavení z laděného procesu do ladicího programu, Visual Studio ukončí Vizualizér.

 Nicméně menší ohrožení zabezpečení stále existuje. Laděného procesu je možné přidružit k druhému ladicímu programu, který byl načten z jiného zdroje (ne do laděného procesu). Strana laděného procesu pak může sdělit, že důvěryhodná strana ladicího programu provede akce jménem. Pokud třída důvěryhodného ladicího programu zpřístupňuje mechanizmus "odstranění tohoto souboru", například laděného procesu s částečným vztahem důvěryhodnosti, může tento mechanismus vyvolat, když uživatel vyvolá svůj Vizualizér.

 Chcete-li zmírnit tuto chybu zabezpečení, je třeba mít na vědomí rozhraní vystavená vaším Vizualizér.

## <a name="see-also"></a>Viz také
- [Architektura Vizualizátoru](../debugger/visualizer-architecture.md)
- [Postupy: Zápis vizualizéru](create-custom-visualizers-of-data.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
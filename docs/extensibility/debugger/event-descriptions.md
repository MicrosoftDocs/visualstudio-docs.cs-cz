---
title: Popisy událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afcad096b9f2991939b1378e44524c9cd83a9baf
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231031"
---
# <a name="event-descriptions"></a>Popisy událostí
Každý typ události má konkrétní účel.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Z důvodů pro jejich používání a události  
  
|Událost|Popis|  
|-----------|-----------------|  
|Aktivovat události dokumentu|Dojít, když chce ladicího stroje (DE) rozhraní IDE k otevření nebo dokumentu přenést do popředí.|  
|Vázaný zarážku nebo zarážku chybové události|Odesílá se, když je vázán na zarážku nebo když nelze svázat zarážku a vrátí chybu.|  
|Zarážka nevázaných události|Dojít, když vázaná zarážka odpojuje z kódu.|  
|Může dojít k zastavení událostí|Odeslat integrovaného vývojového prostředí k určení, zda uživatel chcete zastavit k určitému bodu v kódu.|  
|Události zarážky|Dojít při dosažení zarážky kód nebo data.|  
|Události textu dokumentu|Dojde ke změně textu v dokumentu. Tyto události se neodesílají prostřednictvím `IDebugEventCallBack2::Event` metody.|  
|Engine vytvoření události|Odesílá se, když modul je poprvé vytvořena.|  
|Vstupní bod události|Odesílá se, když má laděný program spustit jeho inicializační kód a dosáhla své první vstupní bod uživatele.|  
|Události výjimky|Odesílá se, když spuštěný program narazí na výjimku.|  
|Události dokončení vyhodnocení výrazů|Odeslány po dokončení asynchronní výraz hodnocení.|  
|Najít Symbol události|Posílá vždycky, když je DE je potřeba požádat uživatele o nalezení symbolů pro modul.|  
|Načíst události dokončení|Odesílány pouze po dokončení úvodního programového zatížení a první kód je spuštěn v programu.|  
|Zpráva události|Odesílá se, když se uživatelům pošlou zprávy.|  
|Události načtení modulu|Odesílá se, když je nový modul načten nebo byla uvolněna.|  
|Výstupní řetězec události|Odesílá se, když program zapíše výstup ladění.|  
|Vytváření a ničení událostí|Odesílat oznámení vytvoření nebo zničení procesy, programy, vlastnosti, relace a vlákna, integrovaném vývojovém prostředí sady Visual Studio můžete udržovat přehled o stavu programy, který se právě ladí.|  
|Krok dokončení události|Odesílá se, když krok je dokončen.|  
|Události změny názvu vlákna|Odesílá se, když uživatel změní název vlákna.|  
|Události změny název programu|Odesílá se, když uživatel změní název programu.|  
  
## <a name="see-also"></a>Viz také:  
 [Odesílání událostí](../../extensibility/debugger/sending-events.md)
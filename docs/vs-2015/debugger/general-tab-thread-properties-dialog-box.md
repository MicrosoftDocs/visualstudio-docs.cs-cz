---
title: Karta Obecné, dialogové okno vlastností vláken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2777096e13ef649f2a340d3b3cae92d050d9531f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728981"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastností vlákna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijte toto dialogové okno pro další informace o konkrétním vlákně. Zobrazíte dialogovému oknu přesunout fokus [zobrazení vláken](../debugger/threads-view.md) okna, nebo otevřete [zobrazení zpráv](../debugger/messages-view.md) a rozbalení zprávy. Vyberte jakékoli vlákno uzel ve stromu a pak zvolte **vlastnosti** z **zobrazení** nabídky.  
  
 **Vlastností vlákna** dialogové okno obsahuje jedno podokno, **Obecné** kartu. K dispozici jsou následující nastavení:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Název modulu**|Název modulu.|  
|**ID vlákna**|Jedinečné ID tohoto vlákna. Všimněte si, že jsou opakovaně využívána ID vlákna; vlákno identifikují pouze po dobu životnosti toto vlákno.|  
|**ID procesu**|Jedinečný Identifikátor tohoto procesu. Čísla ID procesu jsou opakovaně využívána, takže identifikují proces pouze po dobu životnosti procesu. Typ objektu procesu se vytvoří při spuštění programu. Všechna vlákna v procesu sdílet stejnou adresní prostor a mají přístup ke stejným datům. Zvolte tuto hodnotu a zobrazte vlastnosti ID procesu.|  
|**Stav vlákna**|Aktuální stav vlákna. Používá spuštěných vláken na procesor; vlákno úsporného režimu je pomocí. Připraveno vlákno čeká na použít na procesor, protože není zdarma. Vlákno v přechodném stavu čeká prostředek pro provádění, jako je například čekání na jeho zásobníku spouštění k stránkování v z disku. Vlákno čekání nepotřebuje procesor, protože se čeká na periferní na dokončení operace nebo prostředek pro uvolnění.|  
|**Důvod čekání**|To platí pouze v případě, vlákno je ve stavu čekání. Dvojice událostí se používají ke komunikaci s chráněné subsystémů.|  
|**Čas procesoru**|Celkový Procesorový čas strávený na tento proces a jeho vlákna. Rovno uživatelského času + privilegovaného času.|  
|**Čas uživatele**|Celkový uplynulý čas, který má toto vlákno stráví prováděním kódu v uživatelském režimu. Aplikace jsou spouštěny v uživatelském režimu, stejně jako podsystémy jako správce oken a stroj grafiky.|  
|**Privilegovaného času**|Celkový uplynulý čas, který má toto vlákno stráví prováděním kódu v privilegovaném režimu. Při volání služby systému Windows, služba se spustí často v privilegovaném režimu získat přístup k datům systému privátní. Tato data jsou chráněna před přístupem tím, že vlákna provádění v uživatelském režimu. Může být explicitní volání systému nebo může být implicitní, třeba když dojde k selhání stránky nebo přerušení.|  
|**Uplynulý čas**|Celkový uplynulý čas (v sekundách) toto vlákno byla spuštěna.|  
|**Aktuální priorita**|Aktuální dynamické prioritu tohoto vlákna. Vlákna v rámci procesu můžete zvýšit a snížit své vlastní základní priorita relativní k základní priorita procesu.|  
|**Základní priorita**|Aktuální základní priorita toto vlákno.|  
|**Počáteční adresa**|Spouští se virtuální adresa pro toto vlákno.|  
|**Počítač uživatele**|Čítač programu uživatele pro vlákno.|  
|**Přepnutí kontextu**|Počet přepínače z jednoho vlákna do druhého. Vlákno přepínače může dojít v jediném procesu nebo napříč procesy. Přepnout vlákno může být způsobeno jedno vlákno s dotazem, další informace, nebo je přerušeno při vyšší priorita vlákna připravena ke spuštění vlákna.|




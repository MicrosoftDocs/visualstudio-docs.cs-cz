---
title: 'Chyba: webový server nenalezl požadovaný prostředek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 904d628b09c7add48460273ecaff7d8ac288cbc3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297419"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Chyba: Webový server nenalezl požadovaný prostředek.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Služba IIS kvůli bezpečnostním hlediskům vrátila obecnou chybu.  
  
 Jednou z možných příčin je konfigurace zabezpečení serveru. Služba IIS 6,0 a starší verze používaly doplněk, který se označuje jako URLScan, aby vyfiltroval podezřelé a poškozené požadavky. Služba IIS 7,0 obsahuje integrované filtrování požadavků pro stejný účel. V obou případech může aplikace sady Visual Studio zabránit v ladění serveru.  
  
 Existuje mnoho možných příčin této chyby. Mezi nejběžnější příčiny patří problém s instalací nebo konfigurací služby IIS, konfigurací webu nebo oprávněními v systému souborů. Můžete se pokusit o přístup k prostředku pomocí prohlížeče. V závislosti na tom, jak je služba IIS nakonfigurovaná, možná budete muset použít místní prohlížeč na serveru nebo zkontrolovat protokol chyb služby IIS a získat podrobnou chybovou zprávu.  
  
 Další informace o řešení potíží služby IIS najdete v tématu [Správa a Správa služby IIS](https://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>Viz také  
 [Nástroj zabezpečení nástroje UrlScan](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Chyba: Webový server byl uzamčen a blokuje příkaz DEBUG.](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)

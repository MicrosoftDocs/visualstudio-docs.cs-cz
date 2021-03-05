---
description: Služba IIS kvůli bezpečnostním hlediskům vrátila obecnou chybu.
title: Webový server nenalezl požadovaný prostředek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3509094e25447cedc6e46d7d811d65c39ea83e1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146610"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Chyba: Webový server nenalezl požadovaný prostředek.
Služba IIS kvůli bezpečnostním hlediskům vrátila obecnou chybu.

Jednou z možných příčin je konfigurace zabezpečení serveru. Služba IIS 6,0 a starší verze používaly doplněk, který se označuje jako URLScan, aby vyfiltroval podezřelé a poškozené požadavky. Služba IIS 7,0 obsahuje integrované filtrování požadavků pro stejný účel. V obou případech může aplikace sady Visual Studio zabránit v ladění serveru.

Další možnou příčinou této chyby je, že služba W3SVC pro službu IIS není spuštěna. Ověřte, jestli je tato služba spuštěná (šedá) v okně služby (*Services. msc*).

Existuje mnoho dalších možných příčin této chyby. Mezi nejběžnější příčiny patří problém s instalací nebo konfigurací služby IIS, konfigurací webu nebo oprávněními v systému souborů. Můžete se pokusit o přístup k prostředku pomocí prohlížeče. V závislosti na tom, jak je služba IIS nakonfigurovaná, možná budete muset použít místní prohlížeč na serveru nebo zkontrolovat protokol chyb služby IIS a získat podrobnou chybovou zprávu.

 Další informace o řešení potíží služby IIS najdete v tématu [Správa a Správa služby IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Viz také
- [Chyba: webový server byl uzamčen a blokuje operaci ladění](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)

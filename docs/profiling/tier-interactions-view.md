---
title: Zobrazení interakcí vrstev | Microsoft Docs
description: Přečtěte si, jak Profilování interakce vrstev poskytuje informace o časech spuštění ve funkcích vícevrstvých aplikací, které komunikují s databázemi.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 350810bba477f5a86963862fb496cf05eaf2c810
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963182"
---
# <a name="tier-interactions-view"></a>Zobrazení interakcí vrstev

Profilace interakce vrstev poskytuje další informace o časech spuštění ve funkcích vícevrstvých aplikací, které komunikují s databázemi prostřednictvím [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] . Data jsou shromažďována pouze pro volání synchronních funkcí.

**Požadavky**

- Visual Studio Enterprise

Zobrazení interakcí zobrazuje data interakce vrstev ve dvou podoknech:

- Podokno předlohy je hierarchický strom. Řádek nejvyšší úrovně obsahuje agregovaná data pro databázová připojení [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stránky nebo procesu. Podřízené uzly obsahují agregovaná data pro databázová připojení nadřazeného objektu.

- Po kliknutí na uzel volání databáze v podokně předloha se v podokně podrobností zobrazí data instance volání databáze.

  Čas se zobrazuje jako počet milisekund nebo počet taktů procesoru. Chcete-li změnit zobrazenou časovou jednotku, klikněte na nabídku **nástroje** , klikněte na položku **Možnosti** a potom zvolte jednu z **hodnot zobrazit čas jako** možnosti.

## <a name="master-pane"></a>Podokno předlohy

|Sloupec|Popis|
|------------|-----------------|
|**Název**|– Pro řádek nejvyšší úrovně, název profilované procesu nebo webové stránky.<br />– Pro řádek připojení databáze název serveru, který je hostitelem databáze.|
|**Databáze**|Název databáze (pouze řádky připojení databáze).|
|**Výpočtu**|Celkový počet požadavků, které jsou generovány procesem, webovou stránkou nebo připojením k databázi.|
|**Celkový uplynulý čas**|Celkový čas strávený prováděním jedné žádosti z procesu, webové stránky nebo připojení k databázi.|
|**Maximální uplynulý čas**|Maximální doba strávená prováděním jedné žádosti z procesu, webové stránky nebo připojení k databázi.|
|**Minimální uplynulý čas**|Minimální čas strávený prováděním jedné žádosti z procesu, webové stránky nebo připojení k databázi.|
|**Průměrný uplynulý čas**|Průměrná doba, kterou strávily vykonání požadavku z procesu, webové stránky nebo připojení k databázi.|

## <a name="database-connection-details-pane"></a>Podokno podrobností připojení databáze

|Sloupec|Popis|
|------------|-----------------|
|**Text příkazu**|Dotaz SQL žádosti|
|**Počet dotazů**|Počet, kolikrát se dotaz spustil.|
|**Celkový uplynulý čas**|Celkový čas strávený prováděním instancí dotazu.|
|**Maximální uplynulý čas**|Maximální čas strávený prováděním libovolné instance dotazu.|
|**Minimální uplynulý čas**|Minimální čas strávený prováděním jedné instance dotazu.|
|**Průměrný uplynulý čas**|Průměrná doba strávená prováděním instance dotazu.|

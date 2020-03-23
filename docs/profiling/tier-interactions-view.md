---
title: Zobrazení interakce úrovně | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d188d6c3268c8ee9f066eba1b6a57e469f34a78e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778138"
---
# <a name="tier-interactions-view"></a>Zobrazení interakcí vrstev

Profilování interakce vrstvy poskytuje další informace o době provádění ve funkcích [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]vícevrstvých aplikací, které komunikují s databázemi prostřednictvím . Data jsou shromažďována pouze pro synchronní volání funkcí.

**Požadavky**

- Visual Studio Enterprise

Zobrazení interakce zobrazuje data interakce vrstvy ve dvou podoknech:

- Podokno hlavního serveru je hierarchický strom. Řádek nejvyšší úrovně obsahuje agregovaná data [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pro připojení databáze stránky nebo procesu. Podřízené uzly obsahují agregovaná data pro databázová připojení nadřazeného objektu.

- Po klepnutí na uzel volání databáze v hlavním podokně se v podokně podrobností zobrazí data pro instanci volání databáze.

  Čas se zobrazí jako počet milisekund nebo počet značek hodin procesoru. Chcete-li změnit zobrazenou časovou jednotku, klepněte na nabídku **Nástroje,** klepněte na **položku Možnosti**a pak zvolte jednu z **možností Zobrazit čas.**

## <a name="master-pane"></a>Podokno hlavní ho podokna

|Sloupec|Popis|
|------------|-----------------|
|**Název**|- Pro řádek nejvyšší úrovně název profilovaného procesu nebo webové stránky.<br />- Pro řádek připojení k databázi název serveru, který je hostitelem databáze.|
|**Databáze**|Název databáze (pouze řádky připojení databáze).|
|**Počet**|Celkový počet požadavků, které jsou generovány procesem, webovou stránkou nebo připojením k databázi.|
|**Celkový uplynulý čas**|Celkový čas strávený prováděním jednoho požadavku z procesu, webové stránky nebo připojení k databázi.|
|**Maximální uplynulý čas**|Maximální doba strávená prováděním jednoho požadavku z procesu, webové stránky nebo připojení k databázi.|
|**Min uplynulý čas**|Minimální doba, která je strávena prováděním jednoho požadavku z procesu, webové stránky nebo připojení k databázi.|
|**Vytážný uplynulý čas**|Průměrná doba, která je strávena prováděním požadavku z procesu, webové stránky nebo připojení k databázi.|

## <a name="database-connection-details-pane"></a>Podokno Podrobnosti o připojení k databázi

|Sloupec|Popis|
|------------|-----------------|
|**Text příkazu**|Dotaz SQL požadavku.|
|**Počet dotazů**|Počet spuštění dotazu.|
|**Celkový uplynulý čas**|Celkový čas, který je stráven provádění min. instance dotazu.|
|**Maximální uplynulý čas**|Maximální doba, která je strávena prováděním jedné instance dotazu.|
|**Min uplynulý čas**|Minimální doba, která je strávena prováděním jedné instance dotazu.|
|**Vytážný uplynulý čas**|Průměrná doba, která je strávena provádění instance dotazu.|

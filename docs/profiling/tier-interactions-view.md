---
title: Zobrazení interakce vrstvy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d92144a6b9bd94e23397a033fbbee45bd5aeed4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917764"
---
# <a name="tier-interactions-view"></a>Zobrazení interakcí vrstev

Profilování interakce vrstev poskytuje další informace o časy spuštění funkcí s více vrstvami aplikace, které komunikují s databázemi prostřednictvím [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Data se shromažďují pouze pro synchronní volání.

**Požadavky**

- Visual Studio Enterprise

Zobrazení interakcí zobrazí dat interakce vrstev do dvou podoken:

- V hlavním podokně se hierarchického stromu. Na nejvyšší úrovni řádek obsahuje agregovaná data pro připojení databáze [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stránky nebo proces. Podřízené uzly obsahují agregovaná data pro připojení databáze nadřazeného prvku.

- Po kliknutí na uzel volání databáze v hlavním podokně se zobrazí data pro instanci volání databáze v podokně podrobností.

  Čas se zobrazí jako počet milisekund, nebo počet taktů procesoru. Chcete-li změnit časová jednotka zobrazí, klikněte na tlačítko **nástroje** nabídky, klikněte na tlačítko **možnosti**a pak vyberte jednu z **podle hodnoty času zobrazit** možnosti.

## <a name="master-pane"></a>Hlavní podokno

|Sloupec|Popis|
|------------|-----------------|
|**Jméno**|-Pro řádek nejvyšší úrovně, název profilovaný proces nebo webové stránky.<br />-Pro řádek připojení databáze, název serveru, který je hostitelem databáze.|
|**Databáze**|Název databáze (pouze řádky připojení databáze).|
|**Počet**|Celkový počet požadavků, které jsou generovány podle procesu, webové stránky nebo připojení k databázi.|
|**Celkový uplynulý čas**|Celkový čas strávený spouštěním jakékoli jeden požadavek z procesu, webové stránky nebo připojení k databázi.|
|**Maximální uplynulý čas**|Maximální doba trvání provádění jedné žádosti z procesu, webové stránky nebo připojení k databázi.|
|**Minimální uplynulý čas**|Minimální čas, který byl stráven spouštěním jakékoli jeden požadavek z procesu, webové stránky nebo připojení k databázi.|
|**Průměrný uplynulý čas**|Průměrný čas strávený spouštěním žádost z procesu, webové stránky nebo připojení k databázi.|

## <a name="database-connection-details-pane"></a>Podokno podrobností o připojení databáze

|Sloupec|Popis|
|------------|-----------------|
|**Text příkazu**|Dotaz SQL požadavku.|
|**Počet dotazů**|Počet, kolikrát byl dotaz spuštěn.|
|**Celkový uplynulý čas**|Celkový čas strávený spouštěním instance dotazu.|
|**Maximální uplynulý čas**|Maximální čas, který byl stráven spouštěním jakoukoli jednu instanci dotazu.|
|**Minimální uplynulý čas**|Minimální čas, který byl stráven spouštěním jakoukoli jednu instanci dotazu.|
|**Průměrný uplynulý čas**|Průměrný čas strávený spouštěním instanci dotazu.|
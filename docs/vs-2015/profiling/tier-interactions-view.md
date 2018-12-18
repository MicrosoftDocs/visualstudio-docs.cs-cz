---
title: Zobrazení interakce vrstvy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b69144569738dc09368453faef13f5f38428df2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726159"
---
# <a name="tier-interactions-view"></a>Zobrazení interakcí vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilování interakce vrstev poskytuje další informace o časy spuštění funkcí s více vrstvami aplikace, které komunikují s databázemi prostřednictvím [!INCLUDE[vstecado](../includes/vstecado-md.md)]. Data se shromažďují pouze pro synchronní volání.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
  Zobrazení interakcí zobrazí dat interakce vrstev do dvou podoken:  
  
- V hlavním podokně se hierarchického stromu. Na nejvyšší úrovni řádek obsahuje agregovaná data pro připojení databáze [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránky nebo proces. Podřízené uzly obsahují agregovaná data pro připojení databáze nadřazeného prvku.  
  
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
  
## <a name="database-connection-details-pane"></a>V podokně podrobností připojení databáze  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Text příkazu**|Dotaz SQL požadavku.|  
|**Počet dotazů**|Počet, kolikrát byl dotaz spuštěn.|  
|**Celkový uplynulý čas**|Celkový čas strávený spouštěním instance dotazu.|  
|**Maximální uplynulý čas**|Maximální čas, který byl stráven spouštěním jakoukoli jednu instanci dotazu.|  
|**Minimální uplynulý čas**|Minimální čas, který byl stráven spouštěním jakoukoli jednu instanci dotazu.|  
|**Průměrný uplynulý čas**|Průměrný čas strávený spouštěním instanci dotazu.|




---
title: Přizpůsobení IntelliSense pro RequireJS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b1c32d0096742c2364e5ac3b8afe59b39152b2b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246711"
---
# <a name="customizing-intellisense-for-requirejs"></a>Přizpůsobení IntelliSense pro RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Od verze Visual Studio 2013 Update 4, podpora pro oblíbené soubor RequireJS JavaScript a modulární zavaděč je podporována. RequireJS usnadňuje k definování závislostí mezi moduly kódu a dynamicky načíst moduly jenom v případě potřeby. Při psaní kódu jazyka JavaScript, který používá RequireJS, návrhy IntelliSense bude poskytována pro moduly, že jste na něj odkazovat z vaší definice modulu nebo odkazovat pomocí volání do `require()` z vašeho kódu.  
  
 Ve výchozím nastavení, Visual Studio podporuje velmi základní konfiguraci pro podporu RequireJS, ale je obvyklé nastavit nastavení vlastní konfigurace (to znamená, chcete-li definovat aliasy pro knihovny). Toto téma popisuje různé způsoby, které můžete přizpůsobit Visual Studio pro práci s nastavením vašeho projektu jedinečný.  
  
 Toto téma popisuje, jak:  
  
-   Přizpůsobení RequireJS v projektech ASP.NET  
  
-   Přizpůsobit RequireJS JSProj projekty, které se používají k vytváření aplikací Apache Cordova, aplikace Windows Store a aplikace LightSwitch HTML  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>Přizpůsobení RequireJS v projektech ASP.NET  
 Pokud soubor s názvem require.js odkazuje aktuální soubor JavaScript automaticky povolena podpora pro RequireJS (Další informace najdete v části Určení kontextu technologie IntelliSense v [technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md)). V projektech ASP.NET, odkazující na require.js se obvykle provádí pomocí / / / / / \<odkaz / > direktivy v souboru _references.js.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurovat atribut hlavní data v projektu aplikace ASP.NET  
 Přesně simulovat, jak vaše aplikace bude fungovat, když jej spustíte, je potřeba vědět, jaké soubor nejdřív načíst při nastavování require.js editor jazyka JavaScript. To je typicky nakonfigurován v pomocí souboru HTML aplikace `data-main` atribut na prvek skriptu, který odkazuje require.js, jak je znázorněno zde.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 V tomto příkladu ihned po require.js načtení skriptu odkazovat data-main (js/app.js). Soubor, který je načten okamžitě je nejlepším místem nejdříve nakonfigurovat RequireJS využití (pomocí `require.config()`). Editor jazyka JavaScript zjistit, jaké soubor se má použít pro `data-main` ve vaší aplikaci, přidejte `data-main` atribut a potom upravte / / / / / \<odkaz / > direktiva, která odkazuje na require.js ve vaší aplikaci. Například můžete použít tuto direktivu:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Konfigurace stránka spuštění aplikace v projektu ASP.NET  
 Při spuštění aplikace RequireJS předpokládá, že relativní cesty k souborům (například ".. \\"cest) jsou relativní vzhledem k souboru HTML, který načten require.js knihovny. Při psaní kódu v editoru sady Visual Studio pro projekt ASP.NET, tento úvodní stránky neznámé a bude potřeba říct editoru co úvodní stránka má používat při používání relativních cest k souborům. Chcete-li to provést, přidejte `start-page` atribut vaše / / / / / \<odkaz / > – direktiva.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 `start-page` Atribut určuje adresu URL stránky, jako byste ji v prohlížeči při spuštění aplikace.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>Přizpůsobení v projektech JSProj RequireJS  
 Projekty JSProj (soubory projektu končící příponou .jsproj) se používají při vytváření aplikací pro aplikace Apache Cordova, založený na jazyce HTML aplikace Windows Store nebo HTML aplikace LightSwitch. Na rozdíl od projektů ASP.NET přečtěte si tyto projekty odkazy na soubory JS ze souborů HTML, které existují v projektu. Z tohoto důvodu při úpravách jazyka JavaScript v projektu JSProj, zobrazí se podpora pro RequireJS je povolená, pokud soubor jazyka JavaScript aktuálně upravovaný se odkazuje v jiném souboru HTML, který také odkazuje require.js.  
  
 V souboru projektu JSProj nejsou potřeba přizpůsobení kroky potřebné pro projekty ASP.NET. To znamená, že skript soubory používané aplikací `data-main` atribut na značku skriptu, který odkazuje na require.js konfigurace require.js načtou automaticky. Soubor HTML odkazující na require.js slouží také jako úvodní stránku pro aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)




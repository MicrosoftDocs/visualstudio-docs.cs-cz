---
title: Přizpůsobení technologie IntelliSense pro RequireJS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665886"
---
# <a name="customizing-intellisense-for-requirejs"></a>Přizpůsobení IntelliSense pro RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Počínaje Visual Studio 2013 Update 4 je podporovaná podpora oblíbeného souboru JavaScriptu RequireJS a modulárního zavaděče. RequireJS usnadňuje definování závislostí mezi moduly kódu a k dynamickému načítání modulů pouze v případě potřeby. Při psaní kódu jazyka JavaScript, který používá RequireJS, budou k dispozici návrhy IntelliSense pro moduly, na které jste odkazováni z definice modulu, nebo na odkaz pomocí volání `require()` z kódu v rámci vašeho kódu.

 Ve výchozím nastavení Visual Studio podporuje velmi základní konfiguraci pro podporu RequireJS, ale je běžné postup nastavit vlastní nastavení konfigurace (tedy definovat aliasy pro knihovny). Toto téma popisuje různé způsoby, jak lze přizpůsobit aplikaci Visual Studio pro práci s jedinečným nastavením projektu.

 V tomto tématu se dozvíte, jak:

- Přizpůsobení RequireJS v projektech ASP.NET

- Přizpůsobení RequireJS v projektech JSProj, které se používají k vytváření Apache Cordova aplikací, aplikací pro Windows Store a aplikací HTML LightSwitch

## <a name="customize-requirejs-in-aspnet-projects"></a>Přizpůsobení RequireJS v projektech ASP.NET
 Podpora pro RequireJS je automaticky povolena, když je soubor s názvem require.js odkazován aktuálním souborem JavaScriptu (Další informace naleznete v části určení kontextu technologie IntelliSense v [jazyce JavaScript IntelliSense](../ide/javascript-intellisense.md)). V projektech ASP.NET se při odkazování na require.js obvykle provádí pomocí direktivy/// \<reference/> v rámci _references.js souboru.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurace atributu data-Main v projektu ASP.NET
 Aby bylo možné přesně simulovat, jak bude aplikace při spuštění fungovat, musí editor JavaScriptu při nastavování require.js nejprve znát, který soubor se má načíst. To je obvykle nakonfigurováno v souboru HTML aplikace pomocí `data-main` atributu elementu script, který odkazuje na require.js, jak je znázorněno zde.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 V tomto příkladu je skript, na který odkazuje data – Main (js/app.js), načten ihned po require.js. Soubor, který je načten hned, je nejlepším místem pro první konfiguraci využití RequireJS (pomocí `require.config()` ). Chcete-li sdělit editoru JavaScriptu, který soubor použít pro `data-main` ve vaší aplikaci, přidejte `data-main` atribut a pak upravte direktivu/// \<reference/> , která odkazuje na require.js ve vaší aplikaci. Můžete například použít tuto direktivu:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Konfigurace úvodní stránky aplikace v projektu ASP.NET
 Když je aplikace spuštěná, RequireJS předpokládá, že relativní cesty k souborům (například cesty ".. \\ ") jsou relativní vzhledem k souboru HTML, který načte knihovnu require.js. Při psaní kódu v editoru sady Visual Studio pro projekt ASP.NET je tato Úvodní stránka neznámá a vy budete muset sdělit editoru, jakou úvodní stránku chcete použít při používání relativních cest k souborům. Uděláte to tak, že do `start-page` direktivy///přidáte atribut \<reference/> .

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 `start-page`Atribut určuje adresu URL stránky, která se zobrazí v prohlížeči při spuštění aplikace.

## <a name="customize-requirejs-in-jsproj-projects"></a>Přizpůsobení RequireJS v projektech JSProj
 Projekty JSProj (soubory projektu, které končí příponou. JSProj), se používají při sestavování aplikací pro Apache Cordova, aplikací pro Windows Store v jazyce HTML nebo aplikacích HTML LightSwitch. Na rozdíl od projektů ASP.NET tyto projekty čtou odkazy na soubory. js z souborů HTML, které existují v projektu. Z tohoto důvodu se při úpravách JavaScriptu v projektu JSProj zobrazí podpora pro RequireJS, pokud se momentálně upravovaný soubor JavaScriptu odkazuje v jiném souboru HTML, který také odkazuje na require.js.

 V souboru projektu JSProj nejsou potřebné kroky vlastního nastavení potřebné pro projekty ASP.NET. To znamená, že soubory skriptu používané `data-main` atributem na značce Script, který odkazuje na require.js, jsou automaticky načteny pro konfiguraci require.js. Soubor HTML odkazující na require.js se používá také jako úvodní stránka aplikace.

## <a name="see-also"></a>Viz také
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)

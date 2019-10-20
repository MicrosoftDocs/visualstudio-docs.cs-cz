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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665886"
---
# <a name="customizing-intellisense-for-requirejs"></a>Přizpůsobení IntelliSense pro RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Počínaje Visual Studio 2013 Update 4 je podporovaná podpora oblíbeného souboru JavaScriptu RequireJS a modulárního zavaděče. RequireJS usnadňuje definování závislostí mezi moduly kódu a k dynamickému načítání modulů pouze v případě potřeby. Při psaní kódu jazyka JavaScript, který používá RequireJS, budou k dispozici návrhy IntelliSense pro moduly, na které jste odkazováni z definice modulu, nebo na odkazování pomocí volání `require()` v rámci kódu.

 Ve výchozím nastavení Visual Studio podporuje velmi základní konfiguraci pro podporu RequireJS, ale je běžné postup nastavit vlastní nastavení konfigurace (tedy definovat aliasy pro knihovny). Toto téma popisuje různé způsoby, jak lze přizpůsobit aplikaci Visual Studio pro práci s jedinečným nastavením projektu.

 V tomto tématu se dozvíte, jak:

- Přizpůsobení RequireJS v projektech ASP.NET

- Přizpůsobení RequireJS v projektech JSProj, které se používají k vytváření Apache Cordova aplikací, aplikací pro Windows Store a aplikací HTML LightSwitch

## <a name="customize-requirejs-in-aspnet-projects"></a>Přizpůsobení RequireJS v projektech ASP.NET
 Podpora pro RequireJS se automaticky povolí, když se na soubor s názvem vyžaduje. js odkazuje v aktuálním souboru JavaScriptu (Další informace najdete v části určení kontextu technologie IntelliSense v [JavaScriptu IntelliSense](../ide/javascript-intellisense.md)). V projektech ASP.NET se v souboru _references. js obvykle provádí odkaz na vyžadování požadavku. js pomocí direktivy//> \<reference/.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurace atributu data-Main v projektu ASP.NET
 Aby bylo možné přesně simulovat, jak bude vaše aplikace fungovat, když ji spustíte, musí editor JavaScriptu při nastavování požadavku vyžadovat. js znát, který soubor se má nejdřív načíst. To je obvykle nakonfigurováno v souboru HTML aplikace pomocí atributu `data-main` elementu script, který odkazuje na požadavek. js, jak je znázorněno zde.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 V tomto příkladu je skript, na který odkazuje data – Main (js/App. js), načten ihned po požadavku. js. Soubor, který je načten hned, je nejlepším místem pro první konfiguraci RequireJS využití (pomocí `require.config()`). Chcete-li sdělit Editor jazyka JavaScript, který soubor použít pro `data-main` ve vaší aplikaci, přidejte atribut `data-main` a pak upravte direktivu///\<reference/>, která odkazuje na požadavek. js ve vaší aplikaci. Můžete například použít tuto direktivu:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Konfigurace úvodní stránky aplikace v projektu ASP.NET
 Při spuštění aplikace RequireJS předpokládá, že relativní cesty k souborům (například... \\ "cesty) jsou relativní vzhledem k souboru HTML, který načetl knihovnu vyžadovat. js. Při psaní kódu v editoru sady Visual Studio pro projekt ASP.NET je tato Úvodní stránka neznámá a vy budete muset sdělit editoru, jakou úvodní stránku chcete použít při používání relativních cest k souborům. Chcete-li to provést, přidejte atribut `start-page` do direktivy///\<reference/>.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 Atribut `start-page` Určuje adresu URL stránky, která se zobrazí v prohlížeči při spuštění aplikace.

## <a name="customize-requirejs-in-jsproj-projects"></a>Přizpůsobení RequireJS v projektech JSProj
 Projekty JSProj (soubory projektu, které končí příponou. JSProj), se používají při sestavování aplikací pro Apache Cordova, aplikací pro Windows Store v jazyce HTML nebo aplikacích HTML LightSwitch. Na rozdíl od projektů ASP.NET tyto projekty čtou odkazy na soubory. js z souborů HTML, které existují v projektu. Z tohoto důvodu se při úpravách JavaScriptu v projektu JSProj zobrazí podpora pro RequireJS, pokud se momentálně upravovaný soubor JavaScriptu odkazuje v jiném souboru HTML, který také odkazuje na vyžadování. js.

 V souboru projektu JSProj nejsou potřebné kroky vlastního nastavení potřebné pro projekty ASP.NET. To znamená, že soubory skriptu používané atributem `data-main` ve značce Script, který odkazuje na vyžadovat. js, jsou automaticky načteny pro konfiguraci požadavku. js. Soubor HTML odkazující na vyžádání. js je také použit jako úvodní stránka aplikace.

## <a name="see-also"></a>Viz také
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)

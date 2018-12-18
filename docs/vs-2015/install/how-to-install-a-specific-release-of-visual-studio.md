---
title: 'Postupy: instalace konkrétní verze | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1f8da9b0a577ba7810c3895d9492ce4be7c69cd4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065905"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Postupy: instalace konkrétní verze sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Často aktualizujeme instalačního programu sady Visual Studio tak, aby získat nejaktuálnější a optimalizované verzi naší volitelných funkcí.  Ale pokud chcete nainstalovat starší verze sady Visual Studio 2015 – například před aktualizací 1 vydaná verze sady Visual Studio s podporu iOS, pak je nutné donutit pomocí starší verze svých souborů manifestů funkcí instalačního programu sady Visual Studio. V tomto článku se dozvíte, jak na to.

## <a name="installing-the-current-release"></a>Instalace aktuální verze
 Oproti původní verzi Visual Studio 2015 aktualizovali jsme instalačního modulu a soubory manifestu několikrát.  To znamená, že pokud si stáhnete z instalačního programu webové [stahování sady Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) aktualizovat instalační program nainstaluje nejnovější Visual Studio 2015 webu na počítači čisté, připojené k Internetu, což zahrnuje nejnovější vylepšení produktu stejně jako novější, poslední verze volitelných funkcí a nástrojů.

## <a name="installing-earlier-releases"></a>Instalace starší verze
 Můžete vytvořit a připojit bitovou kopii ISO nebo si můžete stáhnout a spustit instalační program přímo z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) a pak připojte soubor .exe s další parametry příkazového řádku (například /CustomInstallPath, / plný, / InstallSelectableItems/norestart / atd.) Chcete-li řídit, jak Visual Studio nainstaluje.

 Následující tabulka obsahuje některé konkrétní scénáře bodu v čase a potřebné parametry příkazového řádku, které je nutné předat do instalačního programu Enterprise edition. (Stejné parametry budou fungovat s komunity nebo Professional edition instalační programy také).

|Edice sady Visual Studio 2015|Co se má spustit|Použití příkazového řádku|Co instalační program nemá|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (použitím nejnovější veřejné verze)|Visual Studio Enterprise s aktualizací (k dispozici z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Poznámka:** výchozí chování tato instalace nabízí nejnovější volitelné funkce, a proto se nevyžaduje žádné parametry příkazového řádku.|Instalační program sady Visual Studio bude používat nejnovější feed.xml a nainstalovat nejnovější soubory|
|Visual Studio Enterprise Update 3 (původní Update 3 bez jakékoli další aktualizace Update 3 období)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, která byla k dispozici při vydání aktualizací Update 3|
|Visual Studio Enterprise Update 2 (původní Update 2, ale s aktualizacemi tuto předem aktuální aktualizace 3)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, který byl aktuální před vydané s aktualizací Update 3|
|Visual Studio Enterprise (původní Update 2 bez jakékoli další aktualizace Update 2 období)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, která byla k dispozici po vydání aktualizace 2|
|Visual Studio Enterprise Update 1 (původní aktualizace 1, ale s aktualizacemi tuto předem aktuální aktualizaci Update 2)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, který byl aktuální před Update 2 všeobecně dostupné|
|Visual Studio Enterprise Update 1 (původní Update 1 bez jakékoli další aktualizace Update 1 období)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, která byla k dispozici po vydání aktualizace 1|
|Visual Studio Enterprise (původní verzi RTM, ale s aktualizace, který předem aktuální aktualizace 1)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, který byl aktuální než Update 1 vydané|
|Visual Studio Enterprise (původní RTM s žádné aktualizace)|Visual Studio Enterprise RTM (k dispozici [stránce pro stažení předplatná MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Instalační program sady Visual Studio použije feed.xml, která byla k dispozici po vydání RTM|

> [!IMPORTANT]
>  V závislosti na jazyku, který chcete použít nahraďte "CSY" (pro angličtinu) s jedním z následujících hodnot:
>
> - Kontextová nápověda (pro čínštinu (zjednodušenou))
>   -   Sada CHT (pro čínština (tradiční))
>   -   Sada CSY (pro čeština)
>   -   DEU (pro němčinu)
>   -   Sada ESN (pro španělštinu)
>   -   FRA (pro francouzština)
>   -   Sada ITA (pro italština)
>   -   jpa (pro japonština)
>   -   Sada kor (pro korejština)
>   -   PLK (pro polština)
>   -   PTB (pro portugalština)
>   -   RU (pro ruština)
>   -   REV (pro turečtina)

## <a name="see-also"></a>Viz také
 [Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
---
title: 'Postupy: instalace konkrétní verze | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814558"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Postupy: Instalace konkrétní verze sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instalaci sady Visual Studio aktualizujeme často, takže získáte nejaktuálnější optimalizovanou verzi našich volitelných funkcí.  Pokud ale chcete nainstalovat starší verzi sady Visual Studio 2015, například předběžnou aktualizaci 1 verzi sady Visual Studio s podporou iOS, pak musíte vynutit instalaci sady Visual Studio, aby používala starší verzi jeho souborů manifestu funkce. V tomto článku se dozvíte, jak na to.

## <a name="installing-the-current-release"></a>Instalace aktuální verze
 Od počáteční verze sady Visual Studio 2015 jsme několikrát aktualizovali instalační modul a soubory manifestu.  To znamená, že Pokud stáhnete webový instalační program z webu [soubory ke stažení sady Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) na čistém počítači připojeném k Internetu, nainstaluje instalační program nejnovější aktualizaci sady visual Studio 2015, která zahrnuje nejnovější vylepšení produktu, a také novější, nejnovější verze volitelných funkcí a nástrojů.

## <a name="installing-earlier-releases"></a>Instalace dřívějších verzí
 Můžete buď vytvořit a připojit bitovou kopii ISO, nebo si můžete stáhnout a spustit instalační program přímo z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) a pak připojit soubor. exe k dalším parametrům příkazového řádku (například/CustomInstallPath,/Full,/InstallSelectableItems,/norestart atd.), abyste mohli řídit, jak se Visual Studio nainstaluje.

 Následující tabulka obsahuje některé konkrétní scénáře k určitému časovému okamžiku a nezbytné parametry příkazového řádku, které musíte předat instalačnímu programu edice Enterprise. (Stejné parametry budou fungovat i u instalačních programů komunity nebo Professional Edition.)

|Edice sady Visual Studio 2015|Co spustit|Příkazový řádek, který se má použít|Co nastavení dělá|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (nejnovější veřejná verze)|Visual Studio Enterprise s aktualizacemi (k dispozici z   [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe`**Poznámka:**  Výchozí chování této instalace nabízí nejnovější volitelné funkce, takže nevyžadují žádné parametry příkazového řádku.|Instalační program sady Visual Studio bude používat nejnovější feed.xml a nainstaluje nejnovější soubory.|
|Visual Studio Enterprise Update 3 (původní aktualizace 3 bez aktualizace pro 3 období)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, které byly k dispozici při vydání aktualizace 3.|
|Visual Studio Enterprise Update 2 (původní aktualizace 2, ale s aktualizacemi, které předcházely aktualizaci 3)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, která byla aktuální před vydáním aktualizace 3.|
|Visual Studio Enterprise (původní aktualizace 2 bez aktualizace 2 – posouzení)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, které byly k dispozici při vydání aktualizace Update 2.|
|Visual Studio Enterprise Update 1 (původní aktualizace 1, ale s aktualizacemi, které předcházely aktualizaci 2)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, která byla aktuální před vydáním aktualizace Update 2.|
|Visual Studio Enterprise Update 1 (původní aktualizace 1 bez aktualizace Update 1 – posouzení)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, které byly k dispozici při vydání aktualizace 1.|
|Visual Studio Enterprise (původní verze RTM, ale s aktualizacemi, které předcházely aktualizaci 1)|Visual Studio Enterprise RTM (k dispozici na  [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, která byla aktuální před vydáním aktualizace 1.|
|Visual Studio Enterprise (původní verze RTM bez aktualizací)|Visual Studio Enterprise RTM (k dispozici na [stránce pro stažení předplatných MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Instalační program sady Visual Studio bude používat feed.xml, které byly k dispozici po vydání RTM.|

> [!IMPORTANT]
> V závislosti na jazyku, který chcete použít, nahraďte text "CSY" (pro angličtinu) jednou z následujících hodnot:
>
> - CHS (pro čínštinu (zjednodušenou))
>   - CHT (pro čínštinu (tradiční))
>   - CSY (pro češtinu)
>   - DEU (pro němčinu)
>   - ESN (pro španělštinu)
>   - dopřed (pro francouzštinu)
>   - ita (pro italštinu)
>   - JPA (pro japonštinu)
>   - KOR (pro korejštinu)
>   - PLK (pro polštinu)
>   - PTB (pro portugalštinu)
>   - ru (pro ruštinu)
>   - Rev (pro turečtinu)

## <a name="see-also"></a>Viz také
 [Příručka pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
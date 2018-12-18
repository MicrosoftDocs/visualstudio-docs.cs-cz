---
title: Soukromá data pro sestavy problémů
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21515d6e9841d943cf91799224afdebf8326e07e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836824"
---
# <a name="developer-community-data-privacy"></a>Ochrana osobních údajů komunity vývojářů

Ve výchozím nastavení, všechny informace v problém sestav na [komunity vývojářů](https://developercommunity.visualstudio.com/), včetně všech komentáře a odpovědi, je veřejně viditelné. To je užitečné, protože umožňuje celé komunitě zobrazíte problémů, řešení a řešení, které našli ostatním uživatelům. Pokud máte obavy o ochraně osobních údajů vašich údajů a identity, ale máte možnosti.

## <a name="identity-privacy"></a>Osobní údaje identity

Pokud vám dělají starosti odhalení svoji identitu [vytvořit nový účet Microsoft](https://signup.live.com/) , který nesmí vyzradit žádné podrobnosti o vás. Vytvoření sestavy pomocí tohoto účtu.

## <a name="data-privacy"></a>Ochrana dat

Pokud vám dělají starosti ochrany osobních údajů, neumisťujte všechno, co chcete zachovat privátní v nadpisu nebo obsahu objektu původní sestavy, což je vždy veřejné. Místo toho vytvořte sestavu a Všimněte si, že budete odesílat podrobnosti soukromě v samostatných komentář. Po vytvoření hlášení o problému, můžete určit, kdo může zobrazit odpovědi a přílohy:

1. V sestavě můžete vytvořit zvolte **přidat komentář** k vytvoření soukromého popis problému.

2. V editoru odpovědi pomocí ovládacího prvku níže **odeslat** a **zrušit** tlačítka zadejte cílovou skupinu pro odpovědi. Zvolte **Viewable moderátoři a původní plakát** omezit viditelnost zaměstnancům společnosti Microsoft a sami.

   ![Ovládací prvek ochrany osobních údajů v komunitě vývojářů](media/developer-community-privacy-control.png)

   Pouze lidé, se kterými můžete zadat vidět komentář a všechny Image, odkazy nebo kódu, které jsou v ní. Veškeré odpovědi v části komentáře mají stejnou viditelnost jako původní komentář. To platí i v případě, že ovládací prvek ochrany osobních údajů v odpovědi není správně zobrazit stav zobrazení s omezeným přístupem.

3. Přidáte popis a jakékoli jiné informace, obrázky a přiložené soubory potřebné pro vaše reprodukci. Zvolte **odeslat** tlačítko soukromě odesílat tyto informace.

   > [!NOTE]
   > Existuje omezení připojené soubory na 2 GB a maximálně 10 soubory. Pokud je potřeba nahrát soubor větší, můžete odeslat nové hlášení o problému nebo žádat zaměstnanec společnosti Microsoft v privátní komentář adrese URL pro odeslání.

Chcete-li udržovat vaše osobní údaje a citlivých informací mimo veřejné zobrazení, pečlivě zachovat všechny interakce s Microsoftem k odpovědím v části s omezením viditelnost komentář. Odpovědi na další komentáře může vést k neúmyslně zveřejnit citlivé informace.

## <a name="data-we-collect"></a>Data, které shromažďujeme

Pokud **nahlásit problém** je zahájeno z instalačního programu Visual Studio, shromažďujeme nejnovější protokolu instalace.

Pokud **nahlásit problém** je zahájeno z aplikace Visual Studio shromažďujeme jeden nebo více z následujících typů dat:

- Watson a .NET položky z protokolu událostí

- Soubor protokolu aktivit v paměti Visual Studio

- Nástroj PerfWatson soubory, pokud je povoleno shromažďování Watson, z *VSFeedbackPerfWatsonData* složky

- LiveShare soubory protokolu, pokud existují, z *VSFeedbackVSRTCLogs* složky

- Xamarin soubory protokolu, pokud existují, z *%LOCALAPPDATA%\Xamarin\Logs*

- Soubory protokolu Nuget, pokud existují, z *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- Web ladicí program protokolové soubory, pokud neexistují:

   - *%TEMP%\vscode-Chrome-Debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-Edge-Debug.txt*

- Snímek obrazovky, pokud budete chtít zahrnout

- Nahrávání dat, pokud budete chtít zahrnout záznam, který obsahuje:

   - Kroky pro reprodukci problému

   - Soubor trasování ETL

   - Soubor s výpisem paměti

    > [!NOTE]
    > Můžete odstranit záznam datům, které nechcete odesílat před odesláním do sestavy.

## <a name="see-also"></a>Viz také:

- [Postup ohlášení problému se sadou Visual Studio](how-to-report-a-problem-with-visual-studio-2017.md)
- [Ochrana dat sestavy problém C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
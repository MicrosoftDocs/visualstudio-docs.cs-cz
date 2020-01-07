---
title: Soukromé údaje pro sestavy problémů
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09f3e5fed93cac3a251e4b7cdcaa988e63ff8741
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596265"
---
# <a name="developer-community-data-privacy"></a>Ochrana osobních údajů komunity vývojářů

Ve výchozím nastavení jsou všechny informace o problémech v [komunitě vývojářů](https://developercommunity.visualstudio.com/), včetně všech komentářů a odpovědí, veřejně viditelné. To je užitečné, protože umožňuje celé komunitě zobrazit problémy, řešení a alternativní řešení, která jiní uživatelé našli. Pokud se ale obáváte o soukromí vašich dat nebo identity, máte možnosti.

## <a name="identity-privacy"></a>Ochrana identity

Pokud máte obavy o odhalení vaší identity, [vytvořte novou účet Microsoft](https://signup.live.com/) , která nezveřejňuje žádné podrobnosti o vás. Pomocí tohoto účtu můžete vytvořit sestavu.

## <a name="data-privacy"></a>Ochrana dat

Pokud máte obavy z ochrany osobních údajů, neumísťujte nic, co chcete zachovat soukromě v názvu nebo obsahu počáteční sestavy, která je vždy veřejná. Místo toho vytvořte sestavu a pak si všimněte, že se podrobnosti pošle soukromě v samostatném komentáři. Po vytvoření sestavy problému můžete určit, kdo může zobrazit odpovědi a přílohy:

1. V sestavě, kterou jste vytvořili, vyberte možnost **Přidat komentář** a vytvořte tak soukromý popis problému.

2. V editoru odpovědí použijte ovládací prvek tlačítka **Odeslat** a **Storno** a určete cílovou skupinu pro vaši odpověď. Vyberte **zobrazitelné moderátory a původní plakát** , abyste omezili přehlednost na zaměstnance Microsoftu a sami.

   ![Řízení ochrany osobních údajů na komunitě vývojářů](media/developer-community-privacy-control.png)

   Komentář a všechny obrázky, odkazy nebo kód, které do něj zahrnete, můžou zobrazit jenom lidé, které zadáte. Všechny odpovědi v komentáři mají stejnou viditelnost jako původní komentář. To platí i v případě, že řízení ochrany osobních údajů na odpovědích nezobrazuje správně stav omezené viditelnosti.

3. Přidejte popis a další informace, obrázky a přiložené soubory, které jsou potřeba pro reprodukci. Kliknutím na tlačítko **Odeslat** odešlete tyto informace soukromě.

   > [!NOTE]
   > Pro připojené soubory existuje limit 2 GB a maximálně 10 souborů. Pokud potřebujete nahrát větší soubor, můžete buď Odeslat novou sestavu problému nebo požádat zaměstnance Microsoftu o soukromý komentář.

Aby bylo možné zachovat ochranu osobních údajů a uchovávat citlivé informace z veřejného zobrazení, je nutné zajistit, aby všechny interakce s Microsoftem odpověděly na odpovědi v rámci komentáře s omezeným viditelností. Odpovědi na jiné komentáře mohou způsobit náhodné zveřejnění citlivých informací.

## <a name="data-we-collect"></a>Data, která shromažďujeme

Při zahájení **hlášení problému** z instalační program pro Visual Studio shromažďujeme nejnovější protokol instalace.

Pokud dojde **k zahájení nahlášení problému** ze sady Visual Studio, shromažďujeme jeden nebo více následujících typů dat:

- Položky Watson a .NET z protokolu událostí

- Soubor protokolu aktivit v paměti sady Visual Studio

- Soubory PerfWatson, pokud je povolená kolekce programu Watson

- Soubory protokolu LiveShare, pokud existují

- Soubory protokolu Xamarin, pokud existují

- Soubory protokolu NuGet, pokud existují

- Soubory protokolu webového ladicího programu, pokud existují

- Protokoly a protokoly chyb rozhraní MEF služby Service hub, pokud existují

- Protokoly Pythonu, pokud existují

- Model Windows Forms protokoly, pokud existují

- Snímek obrazovky, pokud se rozhodnete ho zahrnout

- Zaznamenávání dat, pokud se rozhodnete zahrnout záznam, který zahrnuje:

  - Kroky pro reprodukování problému

  - Trasovací soubor ETL

  - Soubor výpisu paměti

> [!NOTE]
> Soubory protokolu, snímky obrazovky a záznamová data se odesílají společnosti Microsoft pouze v případě, že zadáte oprávnění odesláním sestavy problému, se kterou jsou zahrnuty. Můžete si prohlédnout, které soubory jsou zahrnuté v kroku "Souhrn" v okně nahlásit problém (viz snímek obrazovky, který je součástí této poznámky). Shromážděné protokoly a soubory jsou uložené ve složce% Temp% a pravidelně se vyčistí a po každém nahrání. Pokud nechcete do sestavy problému zahrnout protokol, odstraňte před odesláním sestavy soubor ze složky% Temp%.
  > ![nahlásit problém – Shrnutí shromážděných protokolů](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Viz také:

- [Nahlášení problému se sadou Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [C++Zpráva o problému – ochrana osobních údajů](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)

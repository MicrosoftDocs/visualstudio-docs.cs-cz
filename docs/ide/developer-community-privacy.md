---
title: Soukromá data pro hlášení problémů
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
ms.openlocfilehash: 1e87f35778b8aec615410312c0eb7373d4e9969f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75775874"
---
# <a name="developer-community-data-privacy"></a>Ochrana osobních údajů komunity vývojářů

Ve výchozím nastavení jsou všechny informace v hlášeních problémů komunity [vývojářů](https://developercommunity.visualstudio.com/), včetně všech komentářů a odpovědí, veřejně viditelné. To je výhodné, protože umožňuje celé komunitě zobrazit problémy, řešení a řešení, která našli ostatní uživatelé. Pokud se však obáváte o soukromí svých dat nebo identity, máte možnosti.

## <a name="identity-privacy"></a>Ochrana osobních údajů identity

Pokud máte obavy o odhalení své identity, [vytvořte si nový účet Microsoft,](https://signup.live.com/) který nezveřejňuje žádné podrobnosti o vás. Tento účet slouží k vytvoření sestavy.

## <a name="data-privacy"></a>Ochrana osobních údajů

Pokud máte obavy o ochranu osobních údajů, neuvázejte do názvu nebo obsahu původní sestavy, která je vždy veřejná, nic, co chcete zachovat. Místo toho vytvořte sestavu a pak si všimněte, že podrobnosti odešlete soukromě v samostatném komentáři. Po vytvoření sestavy problémů můžete určit, kdo může zobrazit odpovědi a přílohy:

1. V sestavě, kterou jste vytvořili, zvolte **Přidat komentář** a vytvořte soukromý popis problému.

2. V editoru odpovědí zadejte cílovou skupinu pro odpověď pomocí ovládacího prvku pod tlačítky **Odeslat** a **Storno.** Zvolte **Zobrazitelné moderátory a původní plakát,** abyste omezili viditelnost na zaměstnance microsoftu a na sebe.

   ![Kontrola ochrany osobních údajů v komunitě vývojářů](media/developer-community-privacy-control.png)

   Komentář a všechny obrázky, odkazy nebo kód, které do něj zahrnete, uvidí pouze lidé, které zadáte. Všechny odpovědi v komentáři mají stejnou viditelnost jako původní komentář. To platí i v případě, že ovládací prvek ochrany osobních údajů na odpovědi nezobrazuje stav omezené viditelnosti správně.

3. Přidejte popis a další informace, obrázky a přílohy souborů potřebné pro reprodukci. Chcete-li tyto informace odeslat soukromě, zvolte tlačítko **Odeslat.**

   > [!NOTE]
   > K dispozici je limit 2 GB na připojené soubory a maximálně 10 souborů. Pokud potřebujete nahrát větší soubor, můžete buď odeslat novou zprávu o problému, nebo požádat o adresu URL pro nahrání od zaměstnance společnosti Microsoft v soukromém komentáři.

Chcete-li zachovat ochranu osobních údajů a zachovat citlivé informace mimo veřejné zobrazení, dbát na to, aby všechny interakce se společností Microsoft na odpovědi pod viditelnost-omezený komentář. Odpovědi na jiné komentáře mohou způsobit náhodné zveřejnění citlivých informací.

## <a name="data-we-collect"></a>Údaje, které shromažďujeme

Pokud je **nahlásit problém** iniciovaný z Instalační služby sady Visual Studio, shromažďujeme nejnovější protokol instalace.

Pokud je **problém** nahlásit z Visual Studia, shromažďujeme jeden nebo více následujících typů dat:

- Položky Watson a .NET z protokolu událostí

- Soubor protokolu aktivit sady Visual Studio v paměti

- Soubory PerfWatson, pokud je povolena kolekce Watson

- LiveShare soubory protokolu, pokud existují

- Xamarin log soubory, pokud existují

- Nuget soubory protokolu, pokud existují

- Soubory protokolu webového ladicího programu, pokud existují

- Protokoly služby Hub a protokoly chyb MEF, pokud existují

- Python protokoly, pokud existují

- Protokoly formulářů systému Windows, pokud existují

- Snímek obrazovky, pokud se rozhodnete jej zahrnout

- Nahrávání dat, pokud se rozhodnete zahrnout záznam, který zahrnuje:

  - Kroky k reprodukci problému

  - Trasovací soubor ETL

  - Soubor s výpisem stavu paměti

> [!NOTE]
> Soubory protokolů, snímky obrazovky a data záznamu, která odesíláte, mohou výrazně zvýšit schopnost společnosti Microsoft pochopit váš problém a reagovat na ně.  Takže doporučujeme je zahrnout. Za účelem ochrany vašeho soukromí jsou všechny připojené soubory protokolu, snímky obrazovky a záznamová data odesílány společnosti Microsoft pouze v případě, že odešlete oprávnění odesláním hlášení o problému, se kterým jsou zahrnuty. Před odesláním sestavy můžete zjistit, které soubory jsou zahrnuty v kroku Souhrn v okně Nahlásit problém. Soubory systémového protokolu můžete ze sestavy vyloučit zrušením zaškrtnutí políčka Připojit systémové protokoly v kroku Souhrn. Další informace naleznete na následujícím snímku obrazovky. 
  > ![Nahlásit problém – souhrn shromážděných protokolů](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Viz také

- [Jak nahlásit problém s Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [C++ problém sestavy ochrany osobních údajů](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)

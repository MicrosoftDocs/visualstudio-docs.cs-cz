---
title: Nahlášení problému se sadou Visual Studio
description: Zjistěte, jak nahlásit problém se sadou Visual Studio.
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c985d6699c75a78900366204c8bd5275f4c051d
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769929"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak ohlásit problém se sadou Visual Studio nebo Instalační program pro Visual Studio

> [!NOTE]
> Visual Studio pro Mac najdete v tématu [postup nahlášení problému v Visual Studio pro Mac](/visualstudio/mac/report-a-problem).

Problém můžete nahlásit buď ze sady Visual Studio, nebo z jeho instalačního programu pomocí nástroje zpětné vazby, který je v nich zahrnutý. Nástroj pro zpětnou vazbu vám umožňuje snadno zahrnout diagnostické informace do vašeho názoru a pomáhá týmům v programu Visual Studio diagnostikovat a opravovat problémy mnohem efektivněji. Tady je postup nahlášení problému.

1. **V aplikaci Visual Studio**vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém. K nástroji pro zpětnou vazbu můžete získat přístup také **z nabídky**  >  **Odeslat zpětnou vazbu**  >  **s oznámením o problému**.
![Nahlášení problému v komunitě vývojářů sady Visual Studio ](media/vsfeedbackentry.png) nebo nahlášení problému v **instalační program pro Visual Studio** , pokud nemůžete nainstalovat Visual Studio nebo není možné získat přístup k nástroji pro zpětnou vazbu v sadě Visual Studio.  V instalačním programu vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém.
![Nahlášení problému v komunitě vývojářů sady Visual Studio](media/installer.png)

1. Pokud není přihlášený, vyberte **Přihlásit** se, jak je znázorněno na následujícím snímku obrazovky. Pokud se chcete přihlásit, postupujte podle pokynů na obrazovce.

   ![Přihlášení k nahlášení problému](../ide/media/sign-in-new-ux.png)

   K nahlášení problému stačí jenom v případě, že jste přihlášení, ale můžete také hlasovat a komentovat jakékoli stávající názory.

1. Jakmile se přihlásíte, budete moci zobrazit **problémy** a **aktivitu** na obrazovce **položky** , které sleduji.

   ![Položky, které sleduji](../ide/media/items-i-follow.png)

1. Visual Studio poskytuje rozhraní pro vyhledání vašeho problému a zjištění, jestli ho jiní uživatelé oznámili. Pokud si ji někdo nahlásil, "Hlasujte", abychom nás věděli.
   > [!NOTE]
   > Chcete-li hledat, zadejte požadovaný text do vyhledávacího pole a klikněte na tlačítko zadat nebo stiskněte klávesu ENTER.

   ![Hledání podobných problémů a hlasování](../ide/media/search-and-vote.png)

1. Pokud nenajdete problém, ke kterému jste narazili, v dolní části obrazovky vyberte možnost **ohlásit nový problém** .

1. Vytvořte popisný název problému, který nám pomůže ho směrovat na správný tým sady Visual Studio.

1. Pokud je to možné, uveďte další podrobnosti a připojte postup, abychom mohli problém reprodukovat.

   ![Ohlásit nový problém](../ide/media/report-new-problem.png)

1. Kliknutím na tlačítko **Další** přejdete na kartu **přílohy** . Tady můžete zachytit aktuální obrazovku a odeslat ji do Microsoftu. Chcete-li připojit další snímky obrazovky nebo jiné soubory, vyberte možnost **připojit další soubory**.

   ![Připojení snímku obrazovky k sestavě problému sady Visual Studio](media/report-a-problem-screenshot.png)

1. Pokud nechcete připojit snímek obrazovky nebo [nahrát reprodukci](#record-a-repro), klikněte na tlačítko **Další** a přejděte na kartu **Souhrn** .

1. Vyberte **Odeslat** , pokud chcete odeslat sestavu, včetně všech imagí a souborů trasování nebo výpisu paměti. (Pokud je tlačítko **Odeslat** zobrazeno šedě, ujistěte se, že jste zadali název a popis sestavy.)

   Informace o tom, jaká data se shromažďují, najdete v článku shromažďovaná [data](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Zaznamenání reprodukci

Soubory s výpisem paměti trasování a haldy jsou užitečné při pomoci diagnostikovat problémy. Vážíme si toho, když použijete nástroj **ohlásit problém** k zaznamenání reprodukci kroků a odešlete data do Microsoftu. Tady je postup:

1. Po zadání názvu a popisu problému vyberte **Další** a přejděte na kartu **přílohy** .

1. Vyberte kartu **záznam** .

1. V části **zaznamenat vaše akce**vyberte aktuální instanci sady Visual Studio, pokud zde můžete reprodukování problému. Pokud nemůžete, například pokud je aplikace Visual Studio zavěšena, vyberte **\<Create a new instance>** pro záznam akcí v nové instanci sady Visual Studio.

1. Vyberte **Spustit záznam**. Udělte oprávnění ke spuštění tohoto nástroje.

   ![Výběr možnosti Spustit záznam pro poskytnutí trasování a souboru výpisu haldy v sestavě problému se systémem Visual Studio](../ide/media/record-dialog-box.png)

1. Jakmile se zobrazí nástroj pro **záznam kroků** , proveďte kroky, které reprodukovaly problém.

1. Až budete hotovi, klikněte na tlačítko **Zastavit záznam** .

1. Počkejte několik minut, než sada Visual Studio shromáždí a zabalí informace, které jste si poznamenali.

   Informace o tom, jaká data se shromažďují, najdete v článku shromažďovaná [data](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Když se vyžadují další informace (vyžaduje další informace)

Počínaje verzí Visual Studio 2017 verze 15,5 je k dispozici nový pracovní postup, který uživatelům pomůžou poskytnout další informace o hlášeních o problémech.

1. Když Microsoft inženýr nastavil problém [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) na stav **vyžadovat více informací** , pošle se oznámení v nástroji **ohlásit problém** v sadě Visual Studio oznámení na základě tohoto problému.

   ![V aplikaci Visual Studio je nutné mít k informační oznámení.](../ide/media/nmi-notification.png)

1. Kliknutím na odkaz **Zobrazit problémy** můžete filtrovat a řadit zobrazení na problémy, které vyžadují pozornost. Tyto problémy mají také vedle sebe indikátor, aby je bylo možné odlišit Při obecném vyhledávání.

1. Kliknutím na problém zobrazíte zobrazení Podrobnosti o problému.

   ![Vyžadovat další informace oznámení](../ide/media/nmi-details-view.png)

1. Chcete-li zobrazit žádost o **vyžadování více informací** , klikněte na odkaz **zobrazit jejich žádost a odpověď** v zobrazení Podrobnosti o problému. Zobrazí se dialogové okno s žádostí.

   ![Vyžadovat další informace oznámení](../ide/media/nmi-request.png)

1. Další informace můžete zadat přidáním komentářů, příloh nebo kroků záznamu. Toto prostředí je podobné jako hlášení nového problému nebo poskytnutí dalších informací při hlasování o problému.

1. Žádající pracovník Microsoftu obdrží oznámení o dalších poskytnutých informacích. Pokud mají dostatek informací k prozkoumání, změní se stav problému. V opačném případě se inženýr zeptá ještě více informací.

   > [!NOTE]
   > * Když odpovíte, oznámení zmizí. Místo toho se zobrazí banner, který vás zavede a usnadňuje vám možnost poskytnout ještě více informací.
   > * Jakmile se stav změny změní, oznámení se neukončí pro všechny, kteří se k problému dostanou.
   > * Více než jedna osoba může odpovědět na stejný požadavek **vyžadující více informací** .
   > * V [komunitě vývojářů](https://developercommunity.visualstudio.com/) **nepotřebujeme další** pracovní postup, když k ní přistupujete přímo přes webový prohlížeč, ale můžete tam zadat i komentáře a přílohy.

## <a name="search-for-solutions-or-provide-feedback"></a>Hledání řešení nebo poskytnutí zpětné vazby

Pokud nechcete nebo nemůžete použít aplikaci Visual Studio k nahlášení problému, je pravděpodobné, že problém již byl hlášen a řešení je zveřejněno na stránce [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/) .

Pokud nemáte problém se sestavou, ale chcete navrhnout funkci, je to také místo. Další informace najdete na stránce s [návrhem funkce](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) .

## <a name="see-also"></a>Viz také:

* [Možnosti zpětné vazby v aplikaci Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému s Visual Studio pro Mac](/visualstudio/mac/report-a-problem)
* [Nahlášení problému s C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Komunita vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/)
* [Ochrana osobních údajů komunity vývojářů](developer-community-privacy.md)

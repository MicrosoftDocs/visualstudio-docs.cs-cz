---
title: Jak nahlásit problém s Visual Studio
description: Informace o nahlášení problému s Visual Studio
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
ms.author: seiyer
author: seaniyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97080d4ee2240725f009505cda8429ba8f5975d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "64556722"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak nahlásit problém s Visual Studio nebo Instalační služba sady Visual Studio

> [!NOTE]
> V sadě Visual Studio for Mac najdete [v tématu Jak nahlásit problém ve Visual Studiu pro Mac](/visualstudio/mac/report-a-problem).

Problém můžete nahlásit buď z visual studia nebo jeho instalačního programu pomocí nástroje pro zpětnou vazbu, který je v nich součástí. Nástroj zpětná vazba umožňuje snadno zahrnout diagnostické informace do zpětné vazby a pomáhá týmům sady Visual Studio diagnostikovat a opravovat problémy mnohem efektivněji. Zde jsou kroky k nahlášení problému.

1. **V sadě Visual Studio**vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém. K nástroji pro zpětnou vazbu můžete také získat přístup z nabídky **Nápověda** > **Odeslat zprávu o zpětné** > **vazbě**
![Nahlaste problém v komunitě](media/vsfeedbackentry.png) vývojářů sady Visual Studio Alternativně nahlaste problém v **Instalační službě sady Visual Studio,** pokud nelze nainstalovat visual studio nebo nemáte přístup k nástroji pro zpětnou vazbu v sadě Visual Studio.  V Instalační službě vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém.
![Nahlášení problému v komunitě vývojářů sady Visual Studio](media/installer.png)

1. Pokud se nepřihlásíte, vyberte **Přihlásit se,** jak je znázorněno na následujícím snímku obrazovky. Přihlaste se podle pokynů na obrazovce.

   ![Přihlášení k nahlášení problému](../ide/media/sign-in-new-ux.png)

   Nejen, že můžete nahlásit problém, když jste přihlášeni, ale můžete také hlasovat a komentovat jakoukoli existující zpětnou vazbu.

1. Po přihlášení uvidíte své **problémy** a **aktivitu** na obrazovce **Položky, které sleduji**

   ![Položky, které sleduji](../ide/media/items-i-follow.png)

1. Visual Studio poskytuje rozhraní pro hledání problému a zjistěte, zda ostatní ohlásili. Pokud to někdo nahlásil, "up-vote" to, dejte nám vědět.
   > [!NOTE]
   > Chcete-li hledat, zadejte požadovaný text do vyhledávacího pole a klepněte na tlačítko Enter nebo stiskněte ikonu Hledat.

   ![Hledat a hlasovat pro podobné problémy](../ide/media/search-and-vote.png)

1. Pokud problém, se kterým jste se setkali, nenajdete, zvolte **Nahlásit nový problém** v dolní části obrazovky.

   > [!NOTE]
   > Tlačítko **Nahlásit nový problém** se zobrazí pouze v rozhraní sady Visual Studio pro komunitu vývojářů. Problém nelze nahlásit přímo na webu [komunity vývojářů.](https://developercommunity.visualstudio.com/)

1. Vytvořte popisný název problému, který nám pomáhá směrovat ho do správného týmu sady Visual Studio.

1. Pokud je to možné, uveďte další podrobnosti a připojte postup, abychom mohli problém reprodukovat.

   ![Nahlášení nového problému](../ide/media/report-new-problem.png)

1. Chcete-li přejít na kartu **Přílohy,** vyberte **možnost Další.** Zde můžete zachytit aktuální obrazovku a odeslat ji společnosti Microsoft. Chcete-li připojit další snímky obrazovky nebo jiné soubory, zvolte **Připojit další soubory**.

   ![Připojení snímku obrazovky k sestavě problémů sady Visual Studio](media/report-a-problem-screenshot.png)

1. Pokud nechcete připojit snímek obrazovky nebo [zaznamenat reprodukci](#record-a-repro), vyberte **Další** a přejděte na kartu **Souhrn.**

1. Vyberte **Odeslat,** chcete-li odeslat sestavu spolu se všemi obrázky a soubory trasování nebo výpisu stavu paměti. (Pokud je tlačítko **Odeslat** šedé, ujistěte se, že jste pro sestavu zadali název a popis.)

   Informace o tom, jaké údaje jsou shromažďovány, naleznete [v tématu Údaje, které shromažďujeme](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Záznam repro

Soubory s výpisem trasování a haldy jsou užitečné při diagnostice problémů. Vážíme si toho, když použijete nástroj **Nahlásit problém** k zaznamenání kroků reprodukci a odeslání dat společnosti Microsoft. Postup je:

1. Po zadání názvu a popisu problému vyberte **Další,** abyste se přesunuli na kartu **Přílohy.**

1. Vyberte kartu **Záznam.**

1. V části **Zaznamenat akce**vyberte aktuální instanci sady Visual Studio, pokud můžete problém reprodukovat. Pokud nemůžete, například pokud visual studio je neodpovídá, vyberte ** \<Vytvořit novou instanci>** pro záznam akcí v nové instanci Sady Visual Studio.

1. Vyberte **Možnost Spustit nahrávání**. Udělit oprávnění ke spuštění nástroje.

   ![Zvolte "Spustit nahrávání", chcete-li poskytnout soubor s výpisem trasování a haldy v sestavě problémů sady Visual Studio.](../ide/media/record-dialog-box.png)

1. Po vytvoření nástroje **záznam kroků** proveďte kroky, které problém reprodukují.

1. Až budete hotovi, zvolte tlačítko **Zastavit záznam.**

1. Počkejte několik minut, než visual studio shromáždí a zabalí informace, které jste zaznamenali.

   Informace o tom, jaké údaje jsou shromažďovány, naleznete [v tématu Údaje, které shromažďujeme](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Když jsou zapotřebí další informace (Potřebujete více informací)

Počínaje Visual Studio 2017 verze 15.5, je nový pracovní postup, který pomáhá uživatelům poskytnout další informace o hlášení problémů.

1. Když technik společnosti Microsoft nastaví problém [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) na stav Potřebujete další **informace,** každý uživatel, který odeslal, hlasoval, sledoval nebo komentoval problém, získá oznámení v nástroji **Nahlásit problém** v sadě Visual Studio.

   ![Oznámení o dalších informacích v sadě Visual Studio](../ide/media/nmi-notification.png)

1. Kliknutím na odkaz **Zobrazit problémy** můžete filtrovat a seřadit zobrazení problémů, které vyžadují pozornost. Tyto problémy mají také indikátor vedle nich, aby je odlišily v obecném vyhledávání.

1. Kliknutím na problém zobrazíte zobrazení podrobností o problému.

   ![Potřebujete více informací Oznámení](../ide/media/nmi-details-view.png)

1. Chcete-li zobrazit požadavek **Potřebujete více informací,** klikněte na odkaz **Zobrazit jejich požadavek a odpovědět** v zobrazení podrobností o problému. V dialogovém okně se zobrazí požadavek.

   ![Potřebujete více informací Oznámení](../ide/media/nmi-request.png)

1. Další informace můžete poskytnout přidáním komentářů, příloh nebo kroků záznamu. Tato zkušenost je podobná hlášení nového problému nebo poskytnutí dalších informací při hlasování o problému.

1. Žádající technik společnosti Microsoft obdrží oznámení o dalších poskytnutých informacích. Pokud mají dostatek informací k prozkoumání, stav problému se změní. V opačném případě inženýr požádá o další informace.

   > [!NOTE]
   > * Když odpovíte, oznámení zmizí. Na jeho místě vidíte banner, který vám děkuje a usnadňuje způsob, jak poskytnout ještě více informací.
   > * Jakmile se problém změní stav, oznámení zmizí pro všechny, kteří sledují problém.
   > * Více než jedna osoba může odpovědět na stejnou žádost **Need More Info.**
   > * Při přístupu k komunitě vývojářů neexistuje pracovní postup **Potřeba více informací** v [komunitě vývojářů,](https://developercommunity.visualstudio.com/) ale můžete tam také poskytnout komentáře a přílohy.

## <a name="search-for-solutions-or-provide-feedback"></a>Hledání řešení nebo poskytnutí zpětné vazby

Pokud nechcete nebo nemůžete použít Visual Studio k nahlášení problému, je tu šance, že problém již byl nahlášen a řešení zveřejněné na stránce [Visual Studio Developer Community.](https://developercommunity.visualstudio.com/)

Pokud nemáte problém s nahlášením, ale chcete navrhnout funkci, je pro to také místo. Další informace naleznete na stránce [Navrhnout funkci.](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)

## <a name="see-also"></a>Viz také

* [Možnosti zpětné vazby sady Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému s Visual Studio pro Mac](/visualstudio/mac/report-a-problem)
* [Nahlášení problému s c++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Komunita vývojářů visual studia](https://developercommunity.visualstudio.com/)
* [Ochrana osobních údajů komunity vývojářů](developer-community-privacy.md)

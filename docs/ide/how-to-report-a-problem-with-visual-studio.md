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
ms.openlocfilehash: b2deb3f8ff19c2d7805031c0c3ba02bc82b8a3e7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810871"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak ohlásit problém se sadou Visual Studio nebo Instalační program pro Visual Studio

> [!NOTE]
> Visual Studio pro Mac najdete v tématu [postup nahlášení problému v Visual Studio pro Mac](/visualstudio/mac/report-a-problem).

Problém můžete ohlásit buď ze sady Visual Studio, nebo z jeho instalačního programu. Integrovaný nástroj zpětné vazby umožňuje snadno přidat diagnostické informace, které týmům sady Visual Studio pomáhají diagnostikovat a opravovat problémy. Tady je postup nahlášení problému.

1. **V aplikaci Visual Studio**vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém. K nástroji pro zpětnou vazbu můžete získat přístup také **z nabídky**  >  **Odeslat zpětnou vazbu**  >  **s oznámením o problému**.
![Nahlášení problému v komunitě vývojářů sady Visual Studio ](media/feedback-button.png) nebo nahlášení problému v **instalační program pro Visual Studio** , pokud nemůžete nainstalovat Visual Studio nebo není možné získat přístup k nástroji pro zpětnou vazbu v sadě Visual Studio.  V instalačním programu vyberte ikonu zpětné vazby v pravém horním rohu a vyberte Nahlásit problém.
![Nahlášení problému v komunitě vývojářů sady Visual Studio](media/installer.png)

1. Kliknutím na **nahlásit problém** otevřete váš výchozí prohlížeč a přihlásíte se k němu pomocí stejného účtu, který používáte k přihlášení do sady Visual Studio.

   ![Přihlášení k nahlášení problému](../ide/media/feedback-browser-top.png)

1. Začněte zadáním popisného názvu zprávy o chybě. Musí mít aspoň 25 znaků.

    ![Nahlášení problému](../ide/media/feedback-report.png)

1. Po zahájení psaní se v poli title zobrazí možné duplicity.

    ![Vyhledat duplicity](../ide/media/feedback-search.png)

1. Vyberte možné duplicitní sestavy chyb, abyste viděli, jestli existuje jeden vyhovující problém. Pokud k tomu dojde, Hlasujte místo vytvoření vlastního lístku.

    ![Hlasujte pro duplicity](../ide/media/feedback-duplicate.png)

2. Pokud nebyly nalezeny žádné duplicity, pokračujte zadáním popisu problému. Je důležité, aby bylo co nejblíže jasné, aby bylo možné tuto chybu reprodukována. Nezapomeňte zahrnout jasné kroky reprodukce.

3. Pokud se jedná o zprávu o chybě, poznamenejte si snímek obrazovky zaškrtnutím políčka Zahrnout do sady *Visual Studio screenshot* .

    ![Pořídit snímek obrazovky ](../ide/media/feedback-screenshot.png) *jenom technici Microsoftu, kteří můžou zobrazit snímek obrazovky*

    Snímek obrazovky můžete dokonce oříznout přímo v prohlížeči, abyste mohli odebrat jakékoli citlivé nebo nesouvisející části.

4. Jedním z nejlepších způsobů, jak může technický tým sady Visual Studio problém vyřešit, je poskytnout trasování a soubory s výpisem paměti, aby je bylo možné procházet. Můžete to snadno udělat tak, že zaznamenáte kroky, které vedly k chybě. 

    ![Zaznamenání akcí ](../ide/media/feedback-recording.png) *, které může záznam sledovat pouze technici Microsoftu*

5. Zkontrolujte připojené soubory a nahrajte další soubory, pokud se domníváte, že by to pomohla diagnostikovat problém.   

    ![Připojené soubory – ](../ide/media/feedback-attachments.png) *připojené soubory můžou zobrazit jenom technici Microsoftu* .

6. Posledním krokem je klepnutí na tlačítko **Odeslat** . Odesláním sestavy se pošle přímo do interního systému zasílání zpráv o chybách sady Visual Studio, který čeká na třídění.

## <a name="when-further-information-is-needed"></a>Když je potřeba další informace

Pokud problém neobsahuje důležité informace, přiřadíme stav **potřebuje více informací** . K tomuto problému přiřadíme konkrétní informace, které potřebujeme, a obdržíte e-mailové oznámení. Pokud tyto informace do sedmi dnů neobdržíme, pošleme vám připomenutí. Potom uzavřete lístek po 14 dnech nečinnosti.

1. Použijte odkaz v e-mailu na zprávu o problému nebo přejděte na moji zpětnou vazbu a zobrazte si všechny sestavy ve stavu **vyžaduje více informací** .

    ![Moje zpětná vazba](../ide/media/feedback-my-feedback.png)

1. Kliknutím na odkaz poskytnout další informace v sestavě problém přejdete na novou obrazovku. Tady uvidíte, jaké informace se vyžadují.

   ![Moje zpětná vazba](../ide/media/feedback-need-more-info.png)

1. Další informace můžete zadat přidáním komentářů, příloh nebo kroků záznamu. Toto prostředí je podobné jako hlášení nového problému nebo poskytnutí dalších informací při hlasování o problému.

1. Žádající pracovník Microsoftu obdrží oznámení o dalších poskytnutých informacích. Pokud mají dostatek informací k prozkoumání, změní se stav problému. V opačném případě se inženýr zeptá ještě více informací.

Tyto žádosti vidíte na obrazovce **Moje zpětná vazba** spolu se všemi dalšími **problémy** a **návrhy**.

## <a name="search-for-solutions-or-provide-feedback"></a>Hledání řešení nebo poskytnutí zpětné vazby

Pokud nechcete nebo nemůžete použít aplikaci Visual Studio k nahlášení problému, je pravděpodobné, že problém již byl hlášen a řešení je zveřejněno na stránce [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/) .

Pokud nemáte problém se sestavou, ale chcete navrhnout funkci, je to také místo. Další informace najdete na stránce s [návrhem funkce](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) .

## <a name="see-also"></a>Viz také

* [Pokyny pro komunitu vývojářů](./developer-community-guidelines.md)
* [Možnosti zpětné vazby v aplikaci Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému s Visual Studio pro Mac](/visualstudio/mac/report-a-problem)
* [Nahlášení problému s C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Komunita vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/)
* [Ochrana osobních údajů komunity vývojářů](developer-community-privacy.md)
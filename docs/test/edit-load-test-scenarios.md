---
title: Scénáře zátěžového testu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8fa323d275628fe580763709884552754acfba81
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593236"
---
# <a name="edit-load-test-scenarios"></a>Upravit scénáře zátěžového testu

*Scénář* zátěžového testu určuje vzor zatížení, kombinaci testů, kombinaci prohlížečů a kombinaci sítí. Scénáře jsou důležité, protože umožňují konfigurovat testy simulovat složité, realistické úlohy.

Můžete například testovat web elektronického obchodování, který má internetový front-end používaný stovkami souběžných zákazníků přicházejících při mnoha rychlostech připojení a pomocí různých prohlížečů. Stejný web může mít také funkci správy, kterou používají interní zaměstnanci k aktualizaci produktů a zobrazení statistik. Tito interní uživatelé by obvykle přistupovali k webu pomocí stejného prohlížeče a vysokorychlostního připojení k síti LAN. Měli byste zapouzdřit vlastnosti těchto dvou různých skupin uživatelů v různých scénářích. Každý scénář může obsahovat typ virtuálního uživatele. V tomto případě lze provést scénář zátěžového testu představující virtuální zákazníky a jiný scénář lze provést tak, aby představoval virtuální interní uživatele webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Součásti scénáře

Všechny možnosti počáteční konfigurace a nastavení, které zadáte při vytváření zátěžového testu, lze později v **Editoru zátěžového testu**upravit . Můžete také přidat nové scénáře, spustit nastavení a sady čítačů do zátěžového testu.

![Scénáře zátěžového testu](../test/media/loadtesteditinscenarios.png)

Scénáře obsahují následující součásti:

|Označení|Definice|
|-|-|
|Mix prohlížeče|Simuluje, že virtuální uživatelé přistupují k webu prostřednictvím různých webových prohlížečů.|
|Vzor zatížení|Určuje počet virtuálních uživatelů, kteří jsou aktivní během zátěžového testu, a rychlost, s jakou jsou noví uživatelé spuštěni. Například: krok, konstanta a cíl.For example: step, constant, and goal-based.|
|Model kombinace testů|Určuje pravděpodobnost, že virtuální uživatel spouštějí daný test ve scénáři zátěžového testu. Například: 20% šance ke spuštění TestA a 80% šance ke spuštění TestB. Model kombinace testů by měl odrážet cíle testu pro konkrétní scénář.|
|Testovací směs|Kombinace testů je výběr výkonu webu a testování částí, které tvoří scénář a distribuce těchto testů.|
|Síťový mix|Simuluje, že virtuální uživatelé přistupují k webu prostřednictvím různých síťových připojení. Program Network Mix nabízí možnosti, které zahrnují síť LAN, kabelový modem a další možnosti.|

Scénář má několik dalších vlastností, které můžete upravit pomocí **Editoru zátěžového testu**. Další informace naleznete v [tématu Load test scenario properties](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Přidejte umělé lidské interakce pauzy ve vašem scénáři:** Myslíš, že časy se používají k simulaci lidského chování, které způsobuje, že lidé čekají mezi interakcemi s webovými stránkami. Myslíš, že časy dojít mezi požadavky v testu výkonu webu a mezi iterací testu ve scénáři zátěžového testu. Použití doby přemýšlení v zátěžovém testu může být užitečné při vytváření přesnějších simulací zatížení.|-   [Upravit doby přemýšlení pro simulaci zpoždění interakce s lidmi na webových stránkách](../test/edit-think-times-in-load-test-scenarios.md)|
|**Zadejte počet virtuálních uživatelů pro váš scénář:** Můžete nakonfigurovat vlastnosti vzoru zatížení a určit způsob úpravy simulovaného zatížení uživatele během zátěžového testu. Získáte tři předdefinované vzory zatížení: konstantní, krok a cíl.You get three built-in load patterns: constant, step, and goal-based. Můžete zvolit vzor zatížení a upravit vlastnosti na odpovídající úrovně pro cíle zátěžového testu.|-   [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Nakonfigurujte pravděpodobnost, že virtuální uživatel ve scénáři svede test:** Můžete použít kombinaci testů, která určuje pravděpodobnost, že virtuální uživatel spouštějící daný test ve scénáři zátěžového testu. To umožňuje simulovat zatížení realističtější. Místo toho, abyste měli pouze jeden pracovní postup prostřednictvím aplikací, můžete mít několik pracovních postupů, což je bližší aproximace toho, jak koncoví uživatelé interagují s vašimi aplikacemi.|-   [Úpravy modelů mixů textu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Přidání nebo odebrání webového výkonu nebo testování částí ze scénáře zátěžového testu:** Můžete přidat nebo odebrat výkon webu nebo testování částí z zátěžového testu ve scénáři. Zátěžový test obsahuje jeden nebo více scénářů, z nichž každý obsahuje jeden nebo více testů výkonu webu nebo částí.|-   [Úprava kombinace testů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Nakonfigurujte požadovaný síťový mix pro váš scénář:** Pomocí kombinace sítí můžete simulovat zatížení sítě realističtější ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace typů sítí namísto jednoho typu sítě. Můžete vytvořit bližší aproximaci toho, jak koncoví uživatelé interagují s vašimi aplikacemi. Model kombinace sítí by měl odrážet cíle tohoto scénáře.|-   [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Vyberte příslušnou kombinaci webového prohlížeče pro váš scénář:** Pomocí kombinace prohlížeče můžete simulovat zatížení webu realističtější ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace prohlížečů namísto jednoho prohlížeče. Můžete vytvořit bližší aproximaci prohlížečů, které budou použity s vašimi aplikacemi.|-   [Určení typů webových prohlížečů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Konfigurace nastavení iterace testu pro váš scénář:** Scénář zátěžového testu můžete upravit a nakonfigurovat nastavení iterace testu pomocí editoru zátěžového testu a okna Vlastnosti. Ve výchozím nastavení je scénář nastaven bez maximálních testovacích iterací. Volitelně můžete nakonfigurovat maximální počet iterací ve scénáři a jak dlouho mezi nimi pozastavit.|-   [Konfigurace iterace testů pro scénáře](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Konfigurace nastavení zpoždění pro váš scénář:** Pomocí **editoru zátěžového testu** a okna **Vlastnosti** můžete určit zpoždění před spuštěním scénáře v zátěžovém testu. Příkladem, kdy můžete chtít použít **vlastnost Zpoždění počáteční čas** je, pokud potřebujete jeden scénář začít vyrábět položky, které spotřebovává jiný scénář. Můžete zpozdit náročný scénář povolit vytváření scénář naplnit některá data.|-   [Configureng scénář spuštění zpoždění](../test/configure-scenario-start-delays.md)|
|**Zadejte vzdálené počítače, které mají být používány ve scénáři zátěžového testu:** Po vytvoření zátěžového testu můžete upravit vlastnosti scénáře zátěžového testu a označit tak, které testovací agenty chcete zahrnout. Další informace naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).|-   [Postup: Zadejte testovací agenty, kteří mají být používáni](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Viz také

- [Upravit zátěžové testy](../test/edit-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)

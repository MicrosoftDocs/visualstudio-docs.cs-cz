---
title: Scénáře zátěžového testu
description: Naučte se upravovat scénáře zátěžového testu, které umožňují konfigurovat testy pro simulaci složitých a reálných úloh.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 01129ae017dd51a6bc36d966a495eb7fd1afd2f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926895"
---
# <a name="edit-load-test-scenarios"></a>Upravit scénáře zátěžového testu

*Scénář* zátěžového testu určuje vzor zatížení, kombinaci testů, kombinaci prohlížečů a kombinaci sítí. Scénáře jsou důležité, protože umožňují nakonfigurovat testy pro simulaci složitých a reálných úloh.

Můžete například testovat web elektronického obchodování, který má internetový front-end, který používají stovky souběžných zákazníků, a to v mnoha rychlostech připojení a pomocí různých prohlížečů. Stejný web může mít také funkci správy, kterou používají interní zaměstnanci k aktualizaci produktů a k zobrazení statistik. Tito interní uživatelé by obvykle měli k webu přístup pomocí stejného prohlížeče a vysokorychlostního připojení k síti LAN. Chcete zapouzdřit vlastnosti těchto dvou různých skupin uživatelů v různých scénářích. Každý scénář může obsahovat typ virtuálního uživatele. V takovém případě může být vytvořen scénář zátěžového testu, který představuje virtuální zákazníky a další scénář, který představuje virtuální interní uživatele webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Součásti scénáře

Jakékoli počáteční možnosti konfigurace a nastavení, které zadáte při vytváření zátěžového testu, lze upravit později v **Editor zátěžového testu**. Do zátěžového testu můžete také přidat nové scénáře, parametry spuštění a sady čítačů.

![Scénáře zátěžového testu](../test/media/loadtesteditinscenarios.png)

Scénáře obsahují následující součásti:

|Označení|Definice|
|-|-|
|Kombinace prohlížečů|Simuluje, že virtuální uživatelé přistupují k webu přes nejrůznější webové prohlížeče.|
|Vzor zatížení|Určuje počet virtuálních uživatelů, kteří jsou aktivní během zátěžového testu, a rychlost, s jakou se spouští noví uživatelé. Například: Step, Constant a na základě cílů.|
|Model kombinace testů|Určuje pravděpodobnost, že virtuální uživatel spustí daný test ve scénáři zátěžového testu. Například: 20% šance na spuštění TestA a 80% šance na spuštění TestB. Model kombinace testů by měl odrážet cíle testu pro konkrétní scénář.|
|Kombinace testů|Kombinace testů je výběr testů výkonnosti webu a jednotek, které tvoří scénář, a rozdělení těchto testů.|
|Kombinace sítě|Simuluje, že virtuální uživatelé přistupují k webu prostřednictvím různých síťových připojení. Kombinace sítí nabízí možnosti, které zahrnují LAN, kabelový modem a další možnosti.|

Scénář obsahuje několik dalších vlastností, které můžete upravovat pomocí **Editor zátěžového testu**. Další informace naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Přidání pozastavení umělé lidské interakce ve vašem scénáři:** Časy přemýšlení se používají k simulaci lidského chování, které způsobuje, že lidé budou mezi interakcemi s webem čekat. Časy přemýšlení mezi požadavky v testu výkonnosti webu a mezi testovacími iteracemi ve scénáři zátěžového testu. Použití časů pomýšlení v zátěžovém testu může být užitečné při vytváření přesnějších simulací zatížení.|-   [Úprava časů pomýšlení pro simulaci zpoždění lidské interakce webu](../test/edit-think-times-in-load-test-scenarios.md)|
|**Zadejte počet virtuálních uživatelů pro váš scénář:** Můžete nakonfigurovat vlastnosti vzoru zatížení a určit, jak se během testu zatížení upraví simulované uživatelské zatížení. Získáte tři předdefinované vzory zatížení: konstanta, krok a na základě cílů. Zvolíte vzor zatížení a upravíte vlastnosti na odpovídající úrovně pro vaše cíle zátěžového testu.|-   [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Konfigurace pravděpodobnosti, že virtuální uživatel spustí test ve scénáři:** Můžete použít kombinaci testů, která určuje pravděpodobnost, že virtuální uživatel spustí daný test ve scénáři zátěžového testu. To vám umožní simulovat zatížení realističtějším způsobem. Místo toho, abyste měli v rámci svých aplikací pouze jeden pracovní postup, můžete mít několik pracovních postupů, což je bližší odhad toho, jak koncoví uživatelé pracují s vašimi aplikacemi.|-   [Upravit modely kombinace textu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Přidání nebo odebrání testu výkonnosti webu nebo jednotky z scénáře zátěžového testu:** Můžete přidat nebo odebrat test webového výkonu nebo jednotky z zátěžového testu ve scénáři. Zátěžový test obsahuje jeden nebo více scénářů, z nichž každý obsahuje jeden nebo více testů webového výkonu nebo jednotek.|-   [Upravit kombinaci testů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Nakonfigurujte požadovanou kombinaci sítě pro váš scénář:** Pomocí kombinace sítě můžete simulovat zatížení sítě realističtější ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace typů sítě namísto jednoho typu jednoduché sítě. Vytvoříte blíže přibližné informace o tom, jak koncoví uživatelé pracují s vašimi aplikacemi. Model kombinace sítě by měl odrážet cíle tohoto scénáře.|-   [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Vyberte odpovídající kombinaci webových prohlížečů pro váš scénář:** Pomocí kombinace prohlížečů můžete simulovat webové zatížení realističtější v rámci scénáře zátěžového testu. Načtení se vygeneruje pomocí heterogenní kombinace prohlížečů místo jednoho jediného prohlížeče. Vytvoříte blíže přibližné sblížení prohlížečů, které se budou používat s vašimi aplikacemi.|-   [Zadat typy webových prohlížečů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Nakonfigurujte nastavení iterace testu pro váš scénář:** Můžete upravit scénář zátěžového testu pro konfiguraci nastavení iterace testu pomocí Editor zátěžového testu a okno Vlastnosti. Ve výchozím nastavení je scénář nastaven bez maximálního počtu iterací testu. Volitelně můžete nakonfigurovat maximální počet iterací ve scénáři a dobu pozastavení mezi nimi.|-   [Konfigurace iterací testů pro scénáře](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Nakonfigurujte nastavení zpoždění pro váš scénář:** Pomocí **Editor zátěžového testu** a okna **vlastnosti** můžete zadat zpoždění před spuštěním scénáře v rámci zátěžového testu. Příkladem, kdy může být vhodné použít vlastnost **zpoždění spuštění** , je Pokud potřebujete jeden scénář pro zahájení výroby položek, které jiný scénář spotřebovává. Můžete zpozdit nenáročný scénář a umožnit tak scénáři výroby naplnit nějaká data.|-   [Zpoždění spuštění scénáře Configureng](../test/configure-scenario-start-delays.md)|
|**Zadejte vzdálené počítače, které se mají použít ve scénáři zátěžového testu:** Po vytvoření zátěžového testu můžete upravit vlastnosti scénáře zátěžového testu a určit, které testovací agenty chcete zahrnout. Další informace naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).|-   [Postupy: Určení testovacích agentů k použití](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Viz také

- [Upravit zátěžové testy](../test/edit-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)

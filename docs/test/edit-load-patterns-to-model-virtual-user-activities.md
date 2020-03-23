---
title: Vzory zatížení pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0836fdb085ab33b2a646d9774c94bd859b5ca5ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590303"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů

Vlastnosti vzoru zatížení určují, jak se během zátěžového testu upravuje simulované zatížení uživatele. Visual Studio poskytuje tři předdefinované vzory zatížení: konstantní, krok a na základě cíle. Můžete zvolit vzor zatížení a upravit vlastnosti na odpovídající úrovně pro cíle zátěžového testu.

Vzor zatížení je součástí scénáře. Scénáře, spolu s jejich definované vzory zatížení, zahrnují zátěžový test.

> [!NOTE]
> Ve všech vzorů zatížení zatížení, které generuje Visual Studio je simulované zatížení virtuálních uživatelů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Vzory zátěže

### <a name="constant"></a>Trvalé

Vzorek konstantní zatížení se používá k určení zatížení uživatele, který se nemění během zátěžového testu. Například při spuštění testu kouře na webové aplikace, můžete nastavit světlo, konstantní zatížení 10 uživatelů.

#### <a name="constant-load-pattern-considerations"></a>Aspekty vzorku konstantního zatížení

Vzorek konstantní zatížení se používá ke spuštění stejnézatížení uživatele během spuštění zátěžového testu. Buďte opatrní při používání vzoru konstantní zatížení, který má vysoký počet uživatelů; to může umístit nepřiměřené a nerealistické poptávky na serveru nebo serverech na začátku zátěžového testu. Například pokud zátěžový test obsahuje webový test, který začíná požadavek na domovskou stránku a nastavíte zátěžový test s konstantnízatížení 1 000 uživatelů, zátěžový test odešle prvních 1 000 požadavků na domovskou stránku co nejrychleji. To nemusí být realistická simulace reálného přístupu k vašim webovým stránkám. Chcete-li to zmírnit, zvažte použití vzoru zatížení kroku, který se postupně zvyšuje na 1 000 uživatelů, nebo určete dobu zahřívání v nastavení spuštění zátěžového testu. Pokud je zadána doba zahřívání, zátěžová zkouška automaticky zvýší zatížení postupně během doby zahřívání. Další informace naleznete v [tématu Konfigurace zpoždění spuštění scénáře](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

Vzor zatížení kroku se používá k určení zatížení uživatele, které se zvyšuje s časem až do definovaného maximálního zatížení uživatele. Pro krokování zatížení zadáte **počáteční počet uživatelů**, maximální počet **uživatelů**, doba trvání **kroku (sekundy)** a **počet krokového uživatele**.

Například krok zatížení s **počáteční počet uživatelů** jednoho, Maximální počet **uživatelů** 100, Doba trvání **kroku (sekundy)** 10 a **počet krok uživatele** 1 vytvoří vzor zatížení uživatele, který začíná na 1, zvyšuje o 1 každých 10 sekund, dokud nedosáhne 100 Uživatelů.

> [!NOTE]
> Pokud je celková doba trvání testu kratší než doba potřebná k dosažení maximálního zatížení uživatele, test se zastaví po uplynutí doby trvání a nedosáhne cíle **Maximální počet uživatelů.**

Pomocí cíle Krok můžete zvýšit zatížení, dokud server nedosáhne bodu, kde se výrazně snižuje výkon. S nárůstem zatížení bude serveru nakonec nedostatek prostředků. Načtení kroku je dobrý způsob, jak určit počet uživatelů, u kterých k tomu dochází. S krokování zatížení, budete muset také pečlivě sledovat prostředky agenta a ujistěte se, že agenti mohou generovat požadované zatížení.

Obvykle byste měli provést několik spuštění, které mají různé délky kroku a počet uživatelů kroku, abyste mohli získat dobrá měření pro dané zatížení. Často zatížení zobrazit počáteční špičku pro každý krok jako uživatelé jsou přidány. Držení zatížení při této rychlosti umožňuje měřit výkon systému po obnovení systému z počátečního špičky.

#### <a name="step-load-pattern-considerations"></a>Důležité informace o vzorci zatěžovacího vzoru kroku

Vzor zatížení kroku lze použít ke zvýšení zatížení serveru nebo serverů při spuštění zátěžového testu, takže můžete vidět, jak se liší výkon s nárůstem zatížení uživatele. Chcete-li například zjistit, jak si server nebo servery vedou, když se zatížení uživatele zvyšuje na 2 000 uživatelů, můžete spustit 10hodinový zátěžový test pomocí vzoru načtení kroku, který má následující vlastnosti:

- **Počáteční počet uživatelů:** 100

- **Maximální počet uživatelů:** 2 000

- **Doba trvání kroku (v sekundách):** 1 800

- **Čas krokové rampy (v sekundách):** 20

- **Počet uživatelů kroků**: 100

  Tato nastavení spustit zátěžový test po dobu 30 minut (1 800 sekund) při zatížení uživatele 100, 200, 300 a až 2 000 uživatelů. Vlastnost **Čas čas na dílčí masiv u schodišti** stojí za zvláštní zmínku, protože se jedná pouze o jedinou z těchto vlastností, která není k dispozici pro výběr v **Průvodci novým zátěžovým testem**. Tato vlastnost umožňuje zvýšení z jednoho kroku na další (například od 100 do 200 uživatelů) dojít postupně, nikoli okamžitě. V příkladu by se zatížení uživatele zvýšilo ze 100 na 200 uživatelů během 20 sekund (nárůst o pět uživatelů každou sekundu). Další informace naleznete v [tématu Postup: Určení vlastnosti čas čas krokovou rampou pro vzorek zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Na základě cílů

Vzor zatížení založený na cílech se podobá vzoru kroku, ale upravuje zatížení uživatele na základě prahových hodnot čítače výkonu oproti pravidelným úpravám zatížení uživatele. Zatížení založená na cílech jsou užitečná pro různé účely:

- Maximalizace výstupu z agentů: změřte metriku omezení klíče na agenta, abyste maximalizovali výstup agentů. Obvykle je to CPU; Může to však být také paměť.

- Dosažení některé cílové úrovně prostředků, obvykle CPU, na cílovém serveru, pak měření propustnosti na této úrovni. To umožňuje provést porovnání propustnosti za běhu dané konzistentní úrovní využití prostředků na serveru.

- Dosažení cílové úrovně propustnost na serveru.

  V následující tabulce příklad ukazuje vzor založený na cílech s následujícím nastavením vlastností:

|Skupina vlastností|Vlastnost|Hodnota|
|-|--------------|-|
|Čítač výkonu|Kategorie|Procesor|
|Čítač výkonu|Počítač|Server ContosoServer1|
|Čítač výkonu|Čítač|Procesorový čas v %|
|Čítač výkonu|Instance|_total|
|Cílový rozsah pro čítač výkonu|High-end|90|
|Cílový rozsah pro čítač výkonu|Dolní konec|70|
|Limity počtu uživatelů|Počáteční počet uživatelů|1|
|Limity počtu uživatelů|Maximální počet uživatelů|100|
|Limity počtu uživatelů|Maximální snížení počtu uživatelů|5|
|Limity počtu uživatelů|Maximální přírůstek počtu uživatelů|5|
|Limity počtu uživatelů|Minimální počet uživatelů|1|

Tato nastavení **způsobí, že analyzátor zátěžového testu** upraví zatížení uživatele mezi 1 a 100 během testovacího běhu takovým způsobem, že **čítač** pro `% Processor Time` WebServer01 se pohybuje mezi `70%` a`90%.`

Velikost každého uživatele nastavení zatížení je určena **maximální počet uživatelů přírůstek** a **maximální počet uživatelů snížení** nastavení. Limity počtu uživatelů jsou nastaveny vlastnostmi **Maximální počet uživatelů** a Minimální počet **uživatelů.**

#### <a name="goal-based-load-pattern-considerations"></a>Důležité informace o vzorci zatížení založené na cílech

Vzor zatížení založený na cílech je užitečný, pokud chcete určit počet uživatelů, které může váš systém podporovat, než dosáhne určité úrovně využití prostředků. Tato možnost funguje nejlépe, pokud jste již identifikovali omezující prostředek (to znamená kritické místo) v systému.

Předpokládejme například, že víte, že omezující prostředek v systému je procesor na databázovém serveru a chcete zjistit, kolik uživatelů může být podporováno, když je procesor na databázovém serveru přibližně 75 procent zaneprázdněn. Můžete použít vzor zatížení založený na cílech, který má za cíl zachovat hodnotu čítače výkonu "%Čas procesoru" mezi 70 a 80 procenty.

Jedna věc, kterou je třeba si dát pozor, je, pokud nějaký jiný prostředek omezuje propustnost systému. Tyto prostředky mohou způsobit, že cíle, který je určen vzorem zatížení na základě cíle, nikdy nebude dosaženo. Zatížení uživatele bude také nadále stoupat, dokud není dosaženo hodnoty, která je určena pro **maximální počet uživatelů.** Obvykle se nejedná o požadované zatížení, takže buďte opatrní při výběru čítače výkonu ve vzoru zatížení založeném na cíli.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Určení počátečního vzoru zatížení pro zátěžový test:** Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**vyberete vzor zatížení.|-   [Změna vzoru zatížení](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Úprava vzoru zatížení pro zátěžový test:** Po vytvoření zátěžového testu můžete upravit vzor zatížení v **Editoru zátěžového testu**.|-   [Postup: Určení vlastnosti čas ovou okružní rampu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Určení, zda virtuální uživatelé ve scénáři zátěžového testu mají obsahovat data webové mezipaměti:** Můžete změnit **procento nových Users** vlastnost ovlivnit způsob, jakým zátěžový test simuluje ukládání do mezipaměti webu, které by bylo provedeno webovým prohlížečem pro virtuální uživatele.|-   [Postup: Určení procenta virtuálních uživatelů, kteří používají data webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Určení času krokové rampy pro vzorek zatížení kroku:** **Funkce Čas čas krokové rampy** umožňuje, aby se zvýšení z jednoho kroku na další (například ze 100 na 200 uživatelů) probíhalo postupně, nikoli okamžitě.|-   [Postup: Určení vlastnosti čas ovou okružní rampu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Změna vzoru zatížení

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti vzoru zatížení přidružené ke scénáři na úrovně, které splňují vaše cíle testu.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Vzor zatížení určuje počet virtuálních uživatelů aktivních během zátěžového testu a rychlost, jakou jsou přidáni noví uživatelé. Můžete si vybrat ze tří dostupných vzorů: vzor kroku, konstantní a na základě cíle. Další informace naleznete [v tématu Určení počtu virtuálních uživatelů se vzorky zatížení ve scénáři zátěžového testu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Můžete také změnit vlastnosti zatížení programově pomocí modulu plug-in zátěžového testu. Další informace naleznete v [tématu Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Změna vzoru zatížení

1. Otevřete zátěžový test.

2. V **Editoru zátěžového testu**rozbalte ve složce *Scénáře* scénář, pro který chcete upravit vzor zatížení, a zvolte vzor zatížení pro scénář.

    > [!NOTE]
    > Znění uzlu vzor zatížení, jak je zobrazenve stromu scénáře zátěžového testu, odráží profil zatížení, který jste zvolili při vytváření zátěžového testu. Může to být profil **konstantního zatížení** nebo **profil krokového zatížení**.

3. Stisknutím **klávesy F4** zobrazte okno **Vlastnosti.**

     V okně **Vlastnosti** se zobrazí kategorie **Vzorek zatížení** a **parametry.**

4. (Nepovinné) Změňte **vlastnost Pattern** v kategorii Vzorek **zatížení.**

     Vaše volby pro **Pattern** vlastnost jsou **Krok**, **Konstanta**a **Na základě cíle**. Další informace o typech vzorů zatížení naleznete [v tématu Určení počtu virtuálních uživatelů se vzorky zatížení ve scénáři zátěžového testu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5. (Nepovinné) V kategorii **Parametry** změňte hodnoty.

    > [!NOTE]
    > Hodnoty, které můžete nastavit pro **Parametry,** se liší podle hodnoty, která byla vybrána pro vlastnost **Pattern.**

6. Po dokončení změny vlastností zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test s novým vzorem zatížení.

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Postup: Určení procenta virtuálních uživatelů, kteří používají data webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Postup: Určení vlastnosti čas ovou okružní rampu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)

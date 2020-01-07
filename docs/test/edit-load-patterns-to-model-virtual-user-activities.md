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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590303"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů

Vlastnosti vzorku zatížení určují, jak je upraveno simulované uživatelské zatížení během zátěžového testu. Visual Studio nabízí tři předdefinované vzory zatížení: konstanta, krok a na základě cílů. Zvolíte vzor zatížení a upravíte vlastnosti na odpovídající úrovně pro vaše cíle zátěžového testu.

Vzor zatížení je součástí scénáře. Scénáře spolu s jejich definovanými vzory zatížení tvoří zátěžový test.

> [!NOTE]
> V rámci všech vzorů zatížení je zatížení, které Visual Studio generuje, simulované zatížení virtuálních uživatelů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Vzory zátěže

### <a name="constant"></a>Konstanta

Model konstantního zatížení se používá k určení uživatelského zatížení, které se během zátěžového testu nemění. Například při spuštění testu kouře u webové aplikace můžete chtít nastavit světlo, konstantní zatížení 10 uživatelů.

#### <a name="constant-load-pattern-considerations"></a>Požadavky na konstantní vzor zatížení

Model konstantního zatížení se používá ke spuštění stejného uživatelského zatížení během běhu zátěžového testu. Buďte opatrní při použití modelu konstantního zatížení s vysokým počtem uživatelů; v takovém případě může na serveru nebo serverech na začátku zátěžového testu dojít k nepřiměřené a nereálné poptávce. Například pokud zátěžový test obsahuje webový test, který začíná žádostí na domovskou stránku, a nastavíte zátěžový test s konstantním zatížením 1 000 uživatelů, zátěžový test odešle prvních 1 000 požadavků na domovskou stránku co nejrychlejší. Nemusí se jednat o reálnou simulaci reálného přístupu k vašemu webu. Pokud to chcete zmírnit, zvažte použití vzoru zatížení kroku, který se postupně zvyšuje na 1 000 uživatelů, nebo v nastavení spuštění zátěžového testu zadejte období zahřívání. Pokud je určena doba zahřívání, zátěžový test během období zahřívání automaticky nasadí zatížení postupně. Další informace najdete v tématu [Konfigurace zpoždění spouštění scénářů](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

Vzor zatížení kroku slouží k určení zátěže uživatele, která se zvyšuje s časem až do definovaného maximálního zatížení uživatele. Při načítání krokování zadáte **počáteční počet uživatelů**, **maximální počet uživatelů**, **dobu trvání kroku (sekundy)** a **počet kroků uživatele**.

Například zátěž kroku s **počátečním počtem uživatelů** 1, **maximální počet uživatelů** 100, **Doba trvání kroku (sekundy):** 10 a **Krok počtu uživatelů** 1 vytvoří uživatelský vzor zatížení, který začíná 1, se zvýší o 1 každých 10 sekund, dokud nedosáhne 100 uživatelů.

> [!NOTE]
> Pokud je celková doba trvání testu kratší než čas, který je vyžadován pro krok do maximálního zatížení uživatele, pak se test zastaví po uplynutí doby trvání a nedosáhne **maximálního počtu uživatelů** .

Můžete použít krok cíl ke zvýšení zatížení, dokud server nedosáhne bodu, ve kterém se významně snižuje výkon. Po zvýšení zátěže bude server nakonec vydávat prostředky z provozu. Zátěž kroku je dobrým způsobem, jak zjistit počet uživatelů, na kterých k tomu dojde. S zatížením krokování musíte také monitorovat prostředky agenta pečlivě, abyste se ujistili, že agenti mohou vygenerovat požadované zatížení.

Obvykle byste měli provést několik spuštění, které mají různou dobu trvání a krok počtu uživatelů, abyste mohli pro dané zatížení získat dobré měření. Často se načte počáteční špička pro každý krok, když se přidají uživatelé. Zatížení v této sazbě vám umožní měřit výkon systému po zotavení systému z počátečního špičky.

#### <a name="step-load-pattern-considerations"></a>Pokyny pro vzor zatížení

Vzor zatížení kroku lze použít ke zvýšení zatížení serveru nebo serverů při spuštění zátěžového testu, abyste viděli, jak se výkon mění, protože se zvyšuje zatížení uživatele. Například chcete-li zjistit, jak se server nebo servery provádějí při zvyšování zátěže uživatelů na 2 000 uživatelů, můžete spustit zátěžový test pomocí kroku vzor zatížení, který má následující vlastnosti:

- **Počáteční počet uživatelů**: 100

- **Maximální počet uživatelů**: 2 000

- **Doba trvání kroku (sekundy)** : 1 800

- **Doba rozběhu kroku (sekundy)** : 20

- **Počet kroků uživatele**: 100

  Tato nastavení spustí zátěžový test po dobu 30 minut (1 800 sekund) při načtení uživatele 100, 200, 300 a až 2 000 uživatelů. Vlastnost **Doba** rozjezdu kroku je zvláštní zmínkou, protože se jedná o jedinou jednu z těchto vlastností, která není k dispozici pro výběr v **nové Průvodce zátěžovým testem**. Tato vlastnost umožňuje nárůst od jednoho kroku k dalšímu (například od 100 do 200 uživatelů) k tomu, aby probíhala postupně a nikoli okamžitě. V tomto příkladu se uživatelské zatížení zvýšilo z 100 na 200 uživatelů za 20 sekund období (zvýšení počtu pěti uživatelů každou sekundu). Další informace naleznete v tématu [How to: Určete vlastnost doby rampy kroku pro vzor zatížení](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Založený na cíli

Vzor zatížení založený na cíli se podobá vzoru kroku, ale upravuje zatížení uživatele na základě prahových hodnot čítače výkonu vs. úpravy uživatelských zatížení. Zatížení založená na cíli jsou užitečná pro různé účely:

- Maximalizace výstupu od agentů: změřte klíč omezující metriku agenta, aby se maximalizoval výstup agentů. Obvykle se jedná o procesor; Může to ale být i paměť.

- Dosažení určité úrovně cílového prostředku, obvykle procesoru, na cílovém serveru a následné měření propustnosti na této úrovni. Díky tomu můžete provádět porovnání propustnosti na základě konzistentní úrovně využití prostředků na serveru.

- Dosáhnete cílové úrovně propustnosti na serveru.

  V následující tabulce příklad ukazuje vzor založený na cíli s následujícím nastavením vlastnosti:

|Skupina vlastností|Vlastnost|Hodnota|
|-|--------------|-|
|Čítač výkonu|Kategorie|Procesor|
|Čítač výkonu|Computer|ContosoServer1|
|Čítač výkonu|Counter|% času procesoru|
|Čítač výkonu|instance|_Total|
|Cílový rozsah čítače výkonu|Horní konec|90|
|Cílový rozsah čítače výkonu|Dolní konec|70|
|Omezení počtu uživatelů|Počáteční počet uživatelů|1|
|Omezení počtu uživatelů|Maximální počet uživatelů|100|
|Omezení počtu uživatelů|Maximální snížení počtu uživatelů|5|
|Omezení počtu uživatelů|Maximální přírůstek počtu uživatelů|5|
|Omezení počtu uživatelů|Minimální počet uživatelů|1|

Tato nastavení způsobí, že **analyzátor zátěžového testu** upraví uživatelské zatížení mezi 1 a 100 během testovacího běhu takovým způsobem, že **čítač** pro `% Processor Time` z webserver01 se najede myší na `70%` a `90%.`

Velikost jednotlivých úprav zatížení uživatele je určena **maximálním přírůstkem počtu uživatelů** a **maximálním počtem nastavení pro snížení počtu uživatelů** . Omezení počtu uživatelů se nastavuje podle **maximálního počtu uživatelů** a **minimálních vlastností počtu uživatelů** .

#### <a name="goal-based-load-pattern-considerations"></a>Požadavky na vzor zatížení založené na cíli

Vzor zatížení založený na cíli je užitečný, pokud chcete určit počet uživatelů, které může systém podporovat, než dosáhne určité úrovně využití prostředků. Tato možnost funguje nejlépe, pokud jste již identifikovali omezení prostředku (to znamená kritického bodu) ve vašem systému.

Předpokládejme například, že máte jistotu, že v systému je omezení prostředků procesoru na vašem databázovém serveru a chcete zjistit, kolik uživatelů může být podporováno, pokud je procesor na databázovém serveru přibližně 75 procent zaneprázdněný. Můžete použít model zatížení založený na cíli, který má za cíl zachovat hodnotu čítače výkonu "% času procesoru" mezi 70% a 80 procent.

Jedna z věcí, na kterou se můžete podívat, je, že pokud nějaký jiný prostředek omezuje propustnost systému. Tyto prostředky můžou způsobit, že cíl, který je určený vzorem zatížení podle cíle, nebude nikdy dostupný. Zatížení uživatele bude také pokračovat, dokud nebude dosaženo hodnoty zadané pro **maximální počet uživatelů** . Obvykle se nejedná o požadované zatížení, proto buďte opatrní na výběr čítače výkonu v rámci vzoru zatížení založeného na cíli.

## <a name="tasks"></a>Tasks

|Tasks|Související témata|
|-|-----------------------|
|**Určení počátečního vzoru zatížení pro zátěžový test:** Když vytvoříte zátěžový test pomocí **nového Průvodce zátěžovým testem**, vyberete vzor zatížení.|-   [změnit vzor zatížení](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Úprava vzoru zatížení pro zátěžový test:** Po vytvoření zátěžového testu můžete upravit vzor zatížení v **Editor zátěžového testu**.|-   [Postupy: určení vlastnosti doby rampy kroku pro vzor zatížení](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Určení, zda mají virtuální uživatelé ve scénáři zátěžového testu zahrnovat data webové mezipaměti:** Můžete změnit **procento nových vlastností uživatelů** a ovlivnit tak způsob, jakým zátěžový test simuluje ukládání do mezipaměti webu, které by bylo provedeno webovým prohlížečem pro virtuální uživatele.|-   [Postupy: určení procenta virtuálních uživatelů, kteří používají data mezipaměti webu](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Určení doby trvání kroku pro vzor zatížení kroku:** Vlastnost **Time** probíhající krok umožňuje zvýšit od jednoho kroku k dalšímu (například od 100 do 200 uživatelů), aby se mohlo objevit spíše než hned.|-   [Postupy: určení vlastnosti doby rampy kroku pro vzor zatížení](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Změna vzoru zatížení

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí **Editor zátěžového testu** změnit vlastnosti vzoru zatížení přidružené ke scénáři na úrovně, které splňují vaše cíle testování.

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Vzor zatížení určuje počet virtuálních uživatelů aktivních během zátěžového testu a rychlost, s jakou se přidávají noví uživatelé. Můžete si vybrat ze tří dostupných vzorů: vzor kroku, konstanta a cíl na základě. Další informace najdete v tématu [určení počtu virtuálních uživatelů se vzorci zatížení ve scénáři zátěžového testu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Vlastnosti zatížení lze také změnit programově pomocí modulu plug-in zátěžového testu. Další informace najdete v tématu [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Změna vzoru zatížení

1. Otevřete zátěžový test.

2. V **Editor zátěžového testu**ve složce *scénáře* rozbalte scénář, pro který chcete upravit vzor zatížení a vyberte vzor zatížení pro daný scénář.

    > [!NOTE]
    > Formulace uzlu zátěžového vzoru, jak je zobrazen ve stromu scénáře zátěžového testu, odráží profil zatížení, který jste zvolili při vytváření zátěžového testu. Může to být buď **konstantní profil zatížení** , nebo **profil zatížení kroku**.

3. Stisknutím klávesy **F4** zobrazíte **vlastnosti** okna.

     **Vzor zatížení** a kategorie **parametrů** se zobrazí v okně **vlastnosti** .

4. Volitelné Změňte vlastnost **Pattern** v kategorii **vzor zatížení** .

     Vaše volby pro vlastnost **Pattern** jsou založené na **kroku**, **konstantě**a **cíli**. Další informace o typech vzorů zatížení naleznete v tématu [určení počtu virtuálních uživatelů se vzorci zatížení ve scénáři zátěžového testu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5. Volitelné V kategorii **parametry** změňte hodnoty.

    > [!NOTE]
    > Hodnoty, které lze nastavit pro **parametry** , se liší podle hodnoty, která byla vybrána pro vlastnost **Pattern** .

6. Po dokončení změny vlastností vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test pomocí nového vzoru zatížení.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Postupy: určení procenta virtuálních uživatelů, kteří používají data mezipaměti webu](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Postupy: určení vlastnosti doby rampy kroku pro vzor zatížení](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)

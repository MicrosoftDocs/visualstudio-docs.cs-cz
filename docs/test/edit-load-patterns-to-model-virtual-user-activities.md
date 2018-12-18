---
title: Vzorů zatížení pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a15f771d2afa2b5c8e02eed99b3168a537365a3f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895298"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Úpravy vzorů zatížení pro model aktivity virtuálního uživatele

Vlastnosti vzorku zatížení určují, jak je upraveno simulované uživatelské zatížení během zkušební zatížení. Visual Studio obsahuje tři předdefinované načtené vzorky: Konstanta, krok a cílově zaměřeného vzoru zátížení. Vyberete vzorek zatížení a upravíte vlastnosti odpovídající úrovni pro vaše cíle zátěžového testu.

Vzor zatížení je součástí scénáře. Scénáře, spolu s jejich vzory zatížení definované tvoří zátěžového testu.

> [!NOTE]
> Ve všech vzorech zatížení je zatížení, který generuje sada Visual Studio simulovanou zátěží virtuálních uživatelů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Vzory zátěže

### <a name="constant"></a>Konstanta

 Konstantní zatížení vzorek se používá k určení uživatelské zatížení, který nemění během zátěžového testu. Když spustíte orientačního testování webové aplikace, můžete chtít nastavit světla, konstantní zatížení 10 uživatelů.

#### <a name="constant-load-pattern-considerations"></a>Důležité informace o konstantní zatížení vzorek

 Konstantní zatížení vzorek se používá ke spuštění stejnému zatížení uživatelem při spuštění zátěžového testu. Buďte opatrní při použití konstantního vzoru zatížení s vysokým počtem uživatelů; To uděláte tak mohou klást způsobit nepřiměřený a nereálný požadavek na serveru nebo serverech na začátku zátěžového testu. Například pokud zátěžový test obsahuje test webu, který začíná žádostí na domovskou stránku a nastavíte zkušební zatížení s konstantním zatížením 1 000 uživatelů, zátěžový test odešle prvních 1 000 požadavků na domovskou stránku co nejrychleji. To nemusí být realistická simulace skutečného přístupu na váš web. Chcete-li tento problém zmírnit, zvažte použití kroku vzoru zatížení, který se postupně zvyšuje na 1000 uživatelů, nebo zadejte zahřívání nastavení spuštění zátěžového testu. Pokud je zadán zahřívání, zátěžový test automaticky zvýší zatížení postupně během doby zahřívání. Další informace najdete v tématu [konfigurace zpoždění pro spuštění scénáře](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

 Vzor zatížení kroku slouží k určení uživatelské zatížení, která se zvyšuje s časem až definovaný maximální uživatelské zatížení. Pro krokování zatížení, zadáte **počáteční počet uživatelů**, **maximální počet uživatelů**, **doba trvání kroku (sekundy)**, a **krok počtu uživatelů**.

 Například krokové zatížení pomocí **počáteční počet uživatelů** jednoho, **maximální počet uživatelů** 100, **doba trvání kroku (sekundy)** 10 a **krok počtu uživatelů** 1 vytváří vzor zatížení uživatele, který začíná na 1, se zvýší o 1 každých 10 sekund, dokud nedosáhne 100 uživatelů.

> [!NOTE]
> Pokud doba trvání celkový testu je kratší než čas, který je potřeba krok až do maximální uživatelské zatížení, pak se zastaví po uplynulá doba trvání testu a vůbec nedostane **maximální počet uživatelů** cíl.


 Cílem kroku můžete použít ke zvýšení zatížení, dokud se server dosáhne bod, který kde se výrazně snižuje výkon. Při zvýšení zátěže serveru nakonec dostatek prostředků. Krokové zatížení je dobrým způsobem, jak zjistit počet uživatelů, na kterých k tomu dochází. Při krokování zatížení budete muset také monitorovat prostředky agenta pečlivě sledují a ujistěte se, že agenty můžete generování požadovaného zatížení.

 Obvykle by měl provádět několik běhů, které mají různé krok dob trvání a kroku uživatele se počítá tak, že můžete získat dobrou měření pro dané zatížení. Načtení často, zobrazit počáteční zásobníku pro každý krok, protože se přidají uživatelé. Podniku zatížení v tomto kurzu, můžete po obnovení systému ze zásobníku počáteční měřit výkon systému.

#### <a name="step-load-pattern-considerations"></a>Aspekty vzor zatížení kroku

 Vzor zatížení kroku lze použít ke zvýšení zatížení na serveru nebo serverech při spuštění testu zatížení tak, abyste viděli, jak se mění výkon zvýšením zvýšení zatížení uživatele. Například, pokud chcete zobrazit, jak váš server nebo servery fungují jako zátěž uživatelů zvýší na 2 000 uživatelů, může spustit 10 hodinový zátěžový test pomocí vzor zatížení kroku, který má následující vlastnosti:

- **Počáteční počet uživatelů**: 100

- **Maximální počet uživatelů**: 2000

- **Doba trvání kroku (sekundy)**: víc než 1 800

- **Doba (v sekundách) doběhu kroku**: 20

- **Krok počtu uživatelů**: 100

  Tato nastavení spuštění zátěžového testu po dobu 30 minut (1800 sekund) na uživatele načte 100, 200, 300 a až 2 000 uživatelů. **Doba náběhu kroku** vlastnost je stojí za zvláštní pozornost, protože se jedná pouze jeden z těchto vlastností, které nejsou k dispozici pro výběr v **Průvodce novým zátěžovým testem**. Tato vlastnost umožňuje zvýšení z jednoho kroku do druhého (například z 100 až 200 uživatelů) dochází postupně místo okamžitě. V tomto příkladu uživatelské zatížení by se zvýšilo ze 100 na 200 uživatelů po dobu 20 sekund (zvýšení pěti uživatelů každou sekundu). Další informace najdete v tématu [postupy: určení vlastnosti doby doběhu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Cílově zaměřeného vzoru zátížení

 Cílově zaměřeného vzoru se podobá vzoru kroku ale přizpůsobí uživatelské zatížení na základě prahových hodnot čítačů výkonu a úpravy zatížení pravidelné uživatele. Založeno na cíli zatížení jsou užitečné pro širokou škálu různé účely:

- Maximalizace výstup z agentů: měření klíč omezení metrika agenta pro maximalizaci výstup agentů. Obvykle je procesoru; Však mohou být také paměti.

- Dosažením určité úrovně cílový prostředek, obvykle využití procesoru, na cílovém serveru, pak měření propustnosti na této úrovni. To umožňuje provést porovnání pro spuštění propustnosti přiřazena konzistentní úroveň využití prostředků na serveru.

- Oslovení cílové úrovni propustnosti na serveru.

  V následující tabulce ukazuje příklad cílově zaměřeného vzoru s následujícím nastavením vlastnosti:

|Skupina vlastností|Vlastnost|Hodnota|
|-|--------------|-|
|Čítač výkonu|Kategorie|Procesor|
|Čítač výkonu|Počítače|ContosoServer1|
|Čítač výkonu|Čítač|% Času procesoru|
|Čítač výkonu|instance|_Celkem|
|Cílový rozsah čítače výkonu|Špičkové|90|
|Cílový rozsah čítače výkonu|Nízká kategorie|70|
|Omezení počtu uživatelů|Počáteční počet uživatelů|1|
|Omezení počtu uživatelů|Maximální počet uživatelů|100|
|Omezení počtu uživatelů|Maximální úbytek počtu uživatelů|5|
|Omezení počtu uživatelů|Maximální přírůstek počtu uživatelů|5|
|Omezení počtu uživatelů|Minimální počet uživatelů|1|

 Způsobit, že tato nastavení **Analyzéru zátěžového testu** upravit uživatelské zatížení mezi 1 a 100 během testovacího běhu takovým způsobem, který **čítače** pro `% Processor Time` z WebServer01 pohybuje mezi `70%`a `90%.`

 Velikost jednotlivých úpravu zatížení uživatele se určuje podle **maximální přírůstek počtu uživatelů** a **maximální úbytek počtu uživatelů** nastavení. Omezení počtu uživatel určil institut NIST **maximální počet uživatelů** a **minimální počet uživatelů** vlastnosti.

#### <a name="goal-based-load-pattern-considerations"></a>Důležité informace o cílově zaměřeného vzoru

 Vzorek zatížení založený na cíli je užitečné, když chcete zjistit počet uživatelů, které může systém podporovat před dosažením určité úrovně využití prostředků. Tato možnost funguje nejlépe, když jste již identifikovali omezující zdroj (kritický bod) v systému.

 Předpokládejme například, že víte, že omezující prostředek v systému je využití procesoru na databázovém serveru a chcete zobrazit, kolik uživatelů můžete podporované, když využití procesoru na databázovém serveru je přibližně 75 procent zaneprázdněn. Můžete použít vzorek zatížení založený na cíli, s cílem zachovat hodnotu výkonu čítač "% Processor Time" mezi 70 procent a 80 procent.

 Dávejte pozor na jedna věc je, pokud některé jiné zdroje jsou omezením propustnosti systému. Tyto prostředky může způsobit cíl, který je určen cílově zaměřeného vzoru nikdy dosaženo. Navíc bude pokračovat uživatelské zatížení roste, dokud hodnota, která je určená pro **maximální počet uživatelů** je dosaženo. Obvykle se nejedná o požadované zatížení, proto buďte opatrní při výběru čítače výkonu v cílově zaměřeného vzoru.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Určení vzoru počáteční zatížení pro zátěžový test:** při vytváření zátěžového testu s použitím **nového Průvodce zátěžovým testem**, vyberte vzor zatížení.|-   [Vzor zatížení změňte na](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Úprava vzoru zatížení pro zátěžový test:** po vytvoření zátěžového testu můžete upravit ve vzoru zatížení **editoru zátěžového testu**.|-   [Postupy: určení vlastnosti doby doběhu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Určení, zda virtuálních uživatelů v vašeho zátěžového testu scénáři by měl obsahovat data ve webové mezipaměti:** můžete změnit **procentuální podíl nových uživatelů** vlastnost ovlivňují způsob, ve kterém zátěžový test simuluje webové ukládání do mezipaměti, který by byla prováděna ve webovém prohlížeči pro virtuálního uživatele.|-   [Postupy: určení procentuální podíl virtuálních uživatelů, které používají data ve webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Určení doba doběhu kroku pro vzor zatížení kroku:** **doba náběhu kroku** vlastnost umožňuje zvýšení z jednoho kroku do druhého (například z 100 až 200 uživatelů) dochází postupně místo okamžitě.|-   [Postupy: určení vlastnosti doby doběhu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Vzor zatížení změňte na

 Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti vzorku zatížení přidružené ke scénáři úrovním, které splňují vaše cíle testu.

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).


 Vzor zatížení určuje počet virtuálních uživatelů aktivních během testu zatížení a rychlost, jakou se přidají nové uživatele. Můžete si vybrat z tři dostupné vzorky: krok vzor, konstanty a založeno na cíli. Další informace najdete v tématu [zadat počet virtuálních uživatelů se vzorci zatížení ve scénáři testu zatížení](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Můžete také změnit vlastnosti zatížení prostřednictvím kódu programu pomocí modulu plug-in zátěžového testu. Další informace najdete v tématu [postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md).


### <a name="to-change-the-load-pattern"></a>Chcete-li změnit vzor zatížení

1.  Otevřete zátěžový test.

2.  V **editoru zátěžového testu**v *scénáře* složky, rozbalte scénář, kterou chcete upravit vzoru zatížení pro a vyberete vzorek zatížení pro scénář.

    > [!NOTE]
    > Text uzlu vzor zatížení, který se zobrazí ve stromové struktuře scénář zátěžového testu, odráží profil zatížení, který jste si zvolili při vytváření zátěžového testu. Může být buď **konstantní zatížení profilu** nebo **profilu zatížení kroku**.

3.  Stisknutím klávesy **F4** zobrazíte **vlastnosti** okna.

     **Vzor zatížení** a **parametry** kategorií se zobrazují v **vlastnosti** okna.

4.  (Volitelné) Změnit **vzor** vlastnost **vzor zatížení** kategorie.

     Vaše volby pro **vzor** jsou vlastnosti **krok**, **konstantní**, a **Cílově**. Další informace o typech vzor zatížení, najdete v části [zadat počet virtuálních uživatelů se vzorci zatížení ve scénáři testu zatížení](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (Volitelné) V **parametry** kategorie, změňte hodnoty.

    > [!NOTE]
    > Hodnoty můžete nastavit pro **parametry** se liší podle hodnoty, který byl vybrán pro **vzor** vlastnost.

6.  Po dokončení změn vlastností zvolte **Uložit** na **souboru** nabídky. Můžete spustit zátěžový test pomocí nového vzoru zatížení.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Postupy: určení procentuální podíl virtuálních uživatelů, které používají data ve webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Postupy: určení vlastnosti doby doběhu kroku pro vzor zatížení kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
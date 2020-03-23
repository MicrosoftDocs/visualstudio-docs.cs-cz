---
title: 'Krok 6: Přidání časovače'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23d050df688d4d1efec75245e6f48d748464170c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579323"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Přidání časovače
Dále přidáte <xref:System.Windows.Forms.Timer> ovládací prvek do odpovídající hry. Časovač čeká zadaný počet milisekund a potom vyvolá událost, označovanou jako *značka*. To je užitečné při spuštění akce nebo opakování akce v pravidelných intervalech. V takovém případě můžete pomocí časovače povolit hráči zvolit dvě ikony a pokud se ikony neshodují, po krátké době tyto ikony opět skrýt.

## <a name="to-add-a-timer"></a>Přidání časovače

1. Z panelu nástrojů v **Návrháři formulářů systému Windows**zvolte **Časovač** (v kategorii **Komponenty)** a pak zvolte klávesu **Enter,** nebo poklepáním na časovač přidejte do formuláře ovládací prvek časovače. Ikona časovače s názvem **Timer1**by se měla objevit v prostoru pod formulářem, jak je znázorněno na následujícím obrázku.

     ![Časovač](../ide/media/express_timer.png)<br/>
***Časovač***

    > [!NOTE]
    > Pokud je panel nástrojů prázdný, je nutné před otevřením sady nástrojů vybrat nástroj Návrhář a nikoli kód formuláře.

2. Chcete-li časovač vybrat, zvolte ikonu **Timer1.** V okně **Vlastnosti** přepněte ze zobrazení událostí na vlastnosti zobrazení. Potom nastavte **interval** časovače vlastnost **750**, ale ponechte jeho **Enabled** vlastnost nastavena na **False**. **Vlastnost Interval** sděluje časovači, jak dlouho má čekat mezi *značkami*nebo když aktivuje svou <xref:System.Windows.Forms.Timer.Tick> událost. Hodnota 750 říká časovači, aby před vyvoláním události impulzu čekal tři čtvrtiny sekundy (750 milisekund). Metodu <xref:System.Windows.Forms.Timer.Start> pro spuštění časovače zavoláte až poté, co hráč zvolí druhý štítek.

3. Zvolte ikonu ovládacího prvku časovače v **Návrháři formulářů systému Windows** a pak zvolte klávesu **Enter** nebo poklepejte na časovač a přidejte prázdnou obslužnou rutinu události Tick. Nahraďte kód následujícím kódem, nebo ručně zadejte následující kód do obslužné rutiny události.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Obslužná rutina události Tick provádí tři věci: Nejprve <xref:System.Windows.Forms.Timer.Stop> zajišťuje, že časovač není spuštěn voláním metody. Pak se používá dvě `firstClicked` referenční `secondClicked`proměnné, a , aby se ikony dvou štítků, které hráč zvolil neviditelný znovu. Nakonec obnoví `firstClicked` a `secondClicked` referenční proměnné `null` v jazyce `Nothing` C# a v jazyce Visual Basic. Tento krok je důležitý, protože ukazuje, jak se program sám resetuje. Nyní nesleduje žádné <xref:System.Windows.Forms.Label> ovládací prvky a je připraven pro hráče, aby si znovu vybral štítek.

    > [!NOTE]
    > Timer Objekt má `Start()` metodu, která spustí `Stop()` časovač a metoda, která jej zastaví. Když nastavíte **povolenou** vlastnost časovače na **hodnotu True** v okně **Vlastnosti,** začne tikat, jakmile program začne. Ale když necháte nastavena na **False**, nezačne `Start()` tikat, dokud jeho metoda je volána. Normálně časovač spustí jeho Tick událost znovu a znovu, pomocí **Interval** vlastnost k určení, kolik milisekund čekat mezi značkami. Možná jste si všimli, `Stop()` jak je metoda časovače volána uvnitř tick události. To umístí časovač do *režimu jednoho* `Start()` snímku , což znamená, že při volání metody čeká na zadaný interval, spustí jednu událost Tick a pak se zastaví.

4. Chcete-li zobrazit nový časovač v akci, přejděte do editoru kódu `label_Click()` a přidejte následující kód do horní a dolní části metody obslužné rutiny události. (Přidáváte příkaz `if` na začátek a tři příkazy na konec; zbytek metody zůstane stejný.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kód v horní části metody zkontroluje, zda byl časovač spuštěn kontrolou hodnoty **Vlastnost Ipovač.** Pokud si hráč vybere první a druhý ovládací prvk Label a spustí se časovač, volba třetího štítku nic neudělá.

     Kód v dolní části metody `secondClicked` nastaví referenční proměnnou ke sledování druhého ovládacího prvku Label, který hráč zvolil, a pak nastaví barvu ikony tohoto popisku na černou, aby byla viditelná. Poté spustí časovač v jednorázovém režimu, takže čeká 750 milisekund a potom vyvolá jednu událost impulzu. Obslužná rutina události Tick časovače `firstClicked` skryje dvě ikony a obnoví proměnné a `secondClicked` referenční proměnné, takže formulář je připraven pro hráče vybrat jiný pár ikon.

5. Uložte program a spusťte jej. Vyberte ikonu, která se stane viditelnou.

6. Vyberte jinou ikonu. Objeví se krátce a pak obě ikony zmizí. Tento postup několikrát zopakujte. Formulář nyní sleduje první a druhou ikonu, které jste vybrali, a používá časovač k pozastavení před skrytím ikon.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 7: Zachovat viditelné páry](../ide/step-7-keep-pairs-visible.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 5: Přidání odkazů na popisky](../ide/step-5-add-label-references.md).

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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5958c089998d35dea4324c59f85c368adf900c
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118988"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Přidání časovače
Dále přidáte <xref:System.Windows.Forms.Timer> ovládací prvek do rozrovnávací hry. Časovač počká zadaný počet milisekund a potom vyvolá událost, která je označována jako *Tick*. To je užitečné při spuštění akce nebo opakování akce v pravidelných intervalech. V takovém případě můžete pomocí časovače povolit hráči zvolit dvě ikony a pokud se ikony neshodují, po krátké době tyto ikony opět skrýt.

## <a name="to-add-a-timer"></a>Přidání časovače

1. Ze sady nástrojů v **Návrhář formulářů**zvolte možnost **časovač** (v kategorii **součásti** ) a poté stiskněte klávesu **ENTER** , nebo dvakrát klikněte na časovač a přidejte ovládací prvek časovače do formuláře. Ikona časovače s názvem **Timer1**by se měla objevit v prostoru pod formulářem, jak je znázorněno na následujícím obrázku.

     ![](../ide/media/express_timer.png)
**Časovač** časovače

    > [!NOTE]
    > Pokud je panel nástrojů prázdný, je nutné před otevřením sady nástrojů vybrat nástroj Návrhář a nikoli kód formuláře.

2. Zvolte ikonu **Timer1** a vyberte časovač. V okně **vlastnosti** přepněte ze zobrazení události na zobrazení vlastností. Potom nastavte vlastnost **interval** časovače na **750**, ale nechte vlastnost **Enabled** nastavenou na **hodnotu false**. Vlastnost **interval** určuje, jak dlouho se má čekat mezi *značkami*nebo když vyvolá <xref:System.Windows.Forms.Timer.Tick> událost. Hodnota 750 říká časovači, aby před vyvoláním události impulzu čekal tři čtvrtiny sekundy (750 milisekund). Zavoláte <xref:System.Windows.Forms.Timer.Start> metodu pro spuštění časovače až poté, co hráč zvolí druhý popisek.

3. Zvolte ikonu řízení časovače v **Návrhář formulářů** a pak stiskněte klávesu **ENTER** , nebo poklikejte na časovač a přidejte prázdnou obslužnou rutinu události Tick. Nahraďte kód následujícím kódem, nebo ručně zadejte následující kód do obslužné rutiny události.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

     Obslužná rutina události Tick provádí tři věci: Nejprve se ujistěte, že časovač není spuštěn, voláním <xref:System.Windows.Forms.Timer.Stop> metody. Pak použije dvě referenční proměnné `firstClicked` a `secondClicked`, aby byly ikony dvou popisků, které hráč zvolí jako neviditelný. Nakonec `firstClicked` resetuje referenční proměnné `null` a `secondClicked` v jazyce Visual C# a `Nothing` v Visual Basic. Tento krok je důležitý, protože ukazuje, jak se program sám resetuje. Teď nesleduje žádné <xref:System.Windows.Forms.Label> ovládací prvky a je připravená na to, aby hráč zvolil popisek znovu.

    > [!NOTE]
    > Objekt Timer má `Start()` metodu, která spustí časovač, `Stop()` a metodu, která ji zastaví. Když nastavíte vlastnost Timer **Enabled** na **hodnotu true** v okně **vlastnosti** , začne se začínat hned po zahájení programu. Ale když necháte nastavenou **hodnotu false**, nezačne začínat, dokud není `Start()` volána jeho metoda. V normálním případě časovače aktivuje svou událost Tick přes a znovu pomocí vlastnosti **interval** k určení, kolik milisekund se má čekat mezi značkami. Možná jste si všimli, jak je `Stop()` metoda časovače volána uvnitř události Tick. To znamená, že se časovač vloží do *režimu jednoho snímku*, což `Start()` znamená, že když je metoda volána, počká na zadaný interval, spustí jednu událost Tick a pak se zastaví.

4. Chcete-li zobrazit nový časovač v akci, přejděte do editoru kódu a přidejte následující kód do horní a dolní `label_Click()` části metody obslužné rutiny události. (Přidáváte `if` příkaz na začátek a tři příkazy dole; zbytek metody zůstává stejný.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kód v horní části metody kontroluje, zda byl časovač spuštěn, kontrolou hodnoty vlastnosti **Enabled** . Tímto způsobem, pokud hráč zvolí ovládací prvky prvního a druhého popisku a spustí se časovač, výběr třetího popisku neprovede žádnou možnost.

     Kód v dolní části metody nastaví `secondClicked` referenční proměnnou pro sledování druhého ovládacího prvku popisku, který hráč zvolí, a poté nastaví barvu ikony tohoto popisku na černou, aby byl viditelný. Poté spustí časovač v jednorázovém režimu, takže čeká 750 milisekund a potom vyvolá jednu událost impulzu. Obslužná rutina události Tick časovače skryje dvě ikony a resetuje `firstClicked` proměnné a `secondClicked` reference, takže je formulář připravený na výběr jiného páru ikon.

5. Uložte program a spusťte jej. Vyberte ikonu, která se stane viditelnou.

6. Vyberte jinou ikonu. Objeví se krátce a pak obě ikony zmizí. Tento postup několikrát zopakujte. Formulář nyní sleduje první a druhou ikonu, které jste vybrali, a používá časovač k pozastavení před skrytím ikon.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 7: Zachovat páry viditelné](../ide/step-7-keep-pairs-visible.md)

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 5: Přidejte odkazy](../ide/step-5-add-label-references.md)Label.

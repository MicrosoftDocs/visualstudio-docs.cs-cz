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
ms.openlocfilehash: 4aeb28fe7fbfbaa6e2d120fe58fdc39f188367b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647506"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Přidání časovače
Dále přidáte ovládací prvek <xref:System.Windows.Forms.Timer> do rozrovnávací hry. Časovač počká zadaný počet milisekund a potom vyvolá událost, která je označována jako *Tick*. To je užitečné při spuštění akce nebo opakování akce v pravidelných intervalech. V takovém případě můžete pomocí časovače povolit hráči zvolit dvě ikony a pokud se ikony neshodují, po krátké době tyto ikony opět skrýt.

## <a name="to-add-a-timer"></a>Přidání časovače

1. Ze sady nástrojů v **Návrhář formulářů**zvolte možnost **časovač** (v kategorii **součásti** ) a poté stiskněte klávesu **ENTER** , nebo dvakrát klikněte na časovač a přidejte ovládací prvek časovače do formuláře. Ikona časovače s názvem **Timer1**by se měla objevit v prostoru pod formulářem, jak je znázorněno na následujícím obrázku.

     ![Timer](../ide/media/express_timer.png)<br/>
***Timer***

    > [!NOTE]
    > Pokud je panel nástrojů prázdný, je nutné před otevřením sady nástrojů vybrat nástroj Návrhář a nikoli kód formuláře.

2. Zvolte ikonu **Timer1** a vyberte časovač. V okně **vlastnosti** přepněte ze zobrazení události na zobrazení vlastností. Potom nastavte vlastnost **interval** časovače na **750**, ale nechte vlastnost **Enabled** nastavenou na **hodnotu false**. Vlastnost **interval** určuje, jak dlouho se má čekat mezi *značkami*nebo když vyvolá událost <xref:System.Windows.Forms.Timer.Tick>. Hodnota 750 říká časovači, aby před vyvoláním události impulzu čekal tři čtvrtiny sekundy (750 milisekund). Zavoláte metodu <xref:System.Windows.Forms.Timer.Start>, aby se časovač spouštěl až poté, co hráč zvolí druhý popisek.

3. Zvolte ikonu řízení časovače v **Návrhář formulářů** a pak stiskněte klávesu **ENTER** , nebo poklikejte na časovač a přidejte prázdnou obslužnou rutinu události Tick. Nahraďte kód následujícím kódem, nebo ručně zadejte následující kód do obslužné rutiny události.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Programming jazykové řízení pro ](../ide/media/docs-programming-language-control.png) Docs.Microsoft.com

     Obslužná rutina události Tick provede tři věci: nejprve se ujistěte, že časovač není spuštěn, voláním metody <xref:System.Windows.Forms.Timer.Stop>. Pak pomocí dvou referenčních proměnných, `firstClicked` a `secondClicked`, převede ikony dvou popisků, které hráč zvolí jako neviditelný. Nakonec obnoví `firstClicked` a `secondClicked` referenční proměnné na `null` v C# a `Nothing` v Visual Basic. Tento krok je důležitý, protože ukazuje, jak se program sám resetuje. Teď nesledujete žádné ovládací prvky <xref:System.Windows.Forms.Label> a je připravené, aby hráč znovu zvolil popisek.

    > [!NOTE]
    > Objekt Timer má `Start()` metodu, která spustí časovač, a metodu `Stop()`, která ji zastaví. Když nastavíte vlastnost Timer **Enabled** na **hodnotu true** v okně **vlastnosti** , začne se začínat hned po zahájení programu. Ale když necháte nastavenou **hodnotu false**, nezačne začínat, dokud nebude volána jeho `Start()` metoda. V normálním případě časovače aktivuje svou událost Tick přes a znovu pomocí vlastnosti **interval** k určení, kolik milisekund se má čekat mezi značkami. Možná jste si všimli, jak je metoda časovače `Stop()` volána uvnitř události Tick. To znamená, že se časovač vloží do *režimu jednoho snímku*, což znamená, že když je volána metoda `Start()`, počká na zadaný interval, spustí jednu událost Tick a pak se zastaví.

4. Chcete-li zobrazit nový časovač v akci, přejděte do editoru kódu a přidejte následující kód do horní a dolní části metody obslužné rutiny události `label_Click()`. (Přidáváte do horní části příkaz `if` a do dolní části tři příkazy; zbytek metody zůstává stejný.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kód v horní části metody kontroluje, zda byl časovač spuštěn, kontrolou hodnoty vlastnosti **Enabled** . Tímto způsobem, pokud hráč zvolí ovládací prvky prvního a druhého popisku a spustí se časovač, výběr třetího popisku neprovede žádnou možnost.

     Kód v dolní části metody nastaví `secondClicked` referenční proměnnou pro sledování druhého ovládacího prvku popisku, který hráč zvolí, a poté nastaví barvu ikony tohoto popisku na černou, aby byl viditelný. Poté spustí časovač v jednorázovém režimu, takže čeká 750 milisekund a potom vyvolá jednu událost impulzu. Obslužná rutina události Tick časovače skryje tyto dvě ikony a resetuje `firstClicked` a `secondClicked` referenční proměnné, takže je formulář připravený na to, aby hráč zvolil jiný pár ikon.

5. Uložte program a spusťte jej. Vyberte ikonu, která se stane viditelnou.

6. Vyberte jinou ikonu. Objeví se krátce a pak obě ikony zmizí. Tento postup několikrát zopakujte. Formulář nyní sleduje první a druhou ikonu, které jste vybrali, a používá časovač k pozastavení před skrytím ikon.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md)** .

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md).

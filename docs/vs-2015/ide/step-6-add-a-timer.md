---
title: 'Krok 6: Přidání časovače | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a2d47a66cdedfc191212a178221712de6aefa61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671702"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Přidejte časovač
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dále přidáte řízení **časovače** do porovnávací hry. Časovač počká zadaný počet milisekund a potom vyvolá událost, která je označována jako *Tick*. To je užitečné při spuštění akce nebo opakování akce v pravidelných intervalech. V takovém případě můžete pomocí časovače povolit hráči zvolit dvě ikony a pokud se ikony neshodují, po krátké době tyto ikony opět skrýt.

### <a name="to-add-a-timer"></a>Přidání časovače

1. Ze sady nástrojů v Návrhář formulářů zvolte možnost **časovač** (v kategorii **součásti** ) a poté stiskněte klávesu ENTER, nebo dvakrát klikněte na časovač a přidejte ovládací prvek časovače do formuláře. Ikona časovače s názvem **Timer1**by se měla objevit v prostoru pod formulářem, jak je znázorněno na následujícím obrázku.

     ![Časovač](../ide/media/express-timer.png "Express_Timer") Ukládání

    > [!NOTE]
    > Pokud je panel nástrojů prázdný, je nutné před otevřením sady nástrojů vybrat nástroj Návrhář a nikoli kód formuláře.

2. Zvolte ikonu **Timer1** a vyberte časovač. V okně **vlastnosti** přepněte ze zobrazení události na zobrazení vlastností. Potom nastavte vlastnost **interval** časovače na **750**, ale nechte vlastnost **Enabled** nastavenou na **hodnotu false**. Vlastnost **interval** určuje, jak dlouho se má čekat mezi *značkami*nebo když vyvolá událost Tick. Hodnota 750 říká časovači, aby před vyvoláním události impulzu čekal tři čtvrtiny sekundy (750 milisekund). Zavoláte `Start()` metodu pro spuštění časovače až poté, co hráč zvolí druhý popisek.

3. Zvolte ikonu řízení časovače v Návrhář formulářů a pak stiskněte klávesu ENTER, nebo poklikejte na časovač a přidejte prázdnou obslužnou rutinu události **Tick** . Nahraďte kód následujícím kódem, nebo ručně zadejte následující kód do obslužné rutiny události.

     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]

     Obslužná rutina události Tick provede tři věci: nejprve se ujistěte, že časovač není spuštěn, voláním `Stop()` metody. Pak použije dvě referenční proměnné `firstClicked` a `secondClicked` , aby byly ikony dvou popisků, které hráč zvolí jako neviditelný. Nakonec resetuje `firstClicked` referenční proměnné a v jazyce `secondClicked` `null` Visual C# a `Nothing` v Visual Basic. Tento krok je důležitý, protože ukazuje, jak se program sám resetuje. Teď nesleduje žádné `Label` ovládací prvky a je připravená na to, aby hráč zvolil popisek znovu.

    > [!NOTE]
    > `Timer`Objekt má `Start()` metodu, která spustí časovač, a `Stop()` metodu, která ji zastaví. Když nastavíte vlastnost Timer **Enabled** na **hodnotu true** v okně **vlastnosti** , začne se začínat hned po zahájení programu. Ale když necháte nastavenou **hodnotu false**, nezačne začínat, dokud `Start()` není volána jeho metoda. V normálním případě časovače aktivuje svou událost Tick přes a znovu pomocí vlastnosti **interval** k určení, kolik milisekund se má čekat mezi značkami. Možná jste si všimli, jak `Stop()` je metoda časovače volána uvnitř události Tick. To znamená, že se časovač vloží do *režimu jednoho snímku*, což znamená, že když `Start()` je metoda volána, počká na zadaný interval, spustí jednu událost Tick a pak se zastaví.

4. Chcete-li zobrazit nový časovač v akci, přejděte do editoru kódu a přidejte následující kód do horní a dolní části `label_Click()` metody obslužné rutiny události. (Přidáváte `if` příkaz na začátek a tři příkazy dole; zbytek metody zůstává stejný.)

     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]

     Kód v horní části metody kontroluje, zda byl časovač spuštěn, kontrolou hodnoty vlastnosti **Enabled** . Proto pokud hráč zvolí první a druhý `Label` ovládací prvek a spustí se časovač, výběr třetího popisku neprovede žádné akce.

     Kód v dolní části metody nastaví `secondClicked` referenční proměnnou tak, aby sledovala druhý `Label` ovládací prvek, který hráč zvolil, a poté nastaví barvu ikony tohoto popisku na černou, aby byl viditelný. Poté spustí časovač v jednorázovém režimu, takže čeká 750 milisekund a potom vyvolá jednu událost impulzu. Obslužná rutina události Tick časovače skryje dvě ikony a resetuje `firstClicked` proměnné a `secondClicked` reference, takže je formulář připravený na výběr jiného páru ikon.

5. Uložte program a spusťte jej. Vyberte ikonu, která se stane viditelnou.

6. Vyberte jinou ikonu. Objeví se krátce a pak obě ikony zmizí. Tento postup několikrát zopakujte. Formulář nyní sleduje první a druhou ikonu, které jste vybrali, a používá časovač k pozastavení před skrytím ikon.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md).

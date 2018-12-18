---
title: 'Krok 6: Přidejte časovač'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d02c4d141dd9ec61918600c5fa0b1ca9fadbd9
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748098"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Přidejte časovač
Pak přidáte <xref:System.Windows.Forms.Timer> řízení odpovídající hra. Časovač čeká na zadaný počet milisekund a potom aktivuje událost označuje jako *značek*. To je užitečné při spuštění akce nebo opakování akce v pravidelných intervalech. V takovém případě můžete pomocí časovače povolit hráči zvolit dvě ikony a pokud se ikony neshodují, po krátké době tyto ikony opět skrýt.

## <a name="to-add-a-timer"></a>Přidání časovače

1.  Z panelu nástrojů v **Návrhář formulářů Windows**, zvolte **časovače** (v **součásti** kategorie) a potom zvolte **Enter** klíč, nebo dvakrát klikněte na časovač přidání ovládacího prvku časovač do formuláře. Ikona časovače, nazývá **Timer1**, by se měla objevit v prostoru pod formulářem, jak je znázorněno na následujícím obrázku.

     ![Časovač](../ide/media/express_timer.png)
**časovače**

    > [!NOTE]
    >  Pokud je panel nástrojů prázdný, je nutné před otevřením sady nástrojů vybrat nástroj Návrhář a nikoli kód formuláře.

2.  Vyberte **Timer1** ikonu vyberte časovač. V **vlastnosti** okně přepínat z zobrazování událostí k zobrazení vlastností. Potom nastavte časovače **Interval** vlastnost **750**, ale ponechte jeho **povoleno** vlastnost nastavena na hodnotu **False**. **Interval** vlastnost informuje časovač jak dlouho chcete čekat mezi *rysky*, nebo když se aktivuje její <xref:System.Windows.Forms.Timer.Tick> událostí. Hodnota 750 říká časovači, aby před vyvoláním události impulzu čekal tři čtvrtiny sekundy (750 milisekund). Budete volat <xref:System.Windows.Forms.Timer.Start> metoda spustit časovač až po přehrávač vybere druhý popisek.

3.  Zvolte časovač ikonu ovládacího prvku v **Návrhář formulářů Windows** a potom zvolte **Enter** klíče nebo dvakrát kliknout na časovač pro přidání obslužné rutiny události prázdný značek. Nahraďte kód následujícím kódem, nebo ručně zadejte následující kód do obslužné rutiny události.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

     Obslužné rutiny události značek provádí tři věci: nejdřív zkontroluje, zda časovač neběží voláním <xref:System.Windows.Forms.Timer.Stop> metoda. Potom použije dvě referenční proměnné `firstClicked` a `secondClicked`, aby opět ikony dva štítků, které přehrávač zvolili neviditelná. Nakonec resetuje `firstClicked` a `secondClicked` referenční proměnné na `null` v jazyce Visual C# a `Nothing` v jazyce Visual Basic. Tento krok je důležitý, protože ukazuje, jak se program sám resetuje. Nyní ji není udržuje přehled o žádné <xref:System.Windows.Forms.Label> ovládací prvky a je připravený pro player zvolit štítek znovu.

    > [!NOTE]
    >  Objekt časovače má `Start()` metoda, která spustí časovač, a `Stop()` metoda, která ho zastaví. Když nastavíte časovače **povoleno** vlastnost **True** v **vlastnosti** okně začne tikání ihned zahájí program. Ale když necháte nastavené **False**, nespustí a obaly dokud jeho `Start()` metoda je volána. Za normálních okolností časovač vyvolá událost jeho značek opakovaně, pomocí **Interval** vlastnost určit počet milisekund čekání mezi značky. Jste si všimli jak časovače `Stop()` metoda je volána v rámci značek událostí. Toto vloží časovač do *jeden snímek režim*, což znamená, že pokud `Start()` metoda je volána, čeká na zadaném intervalu, aktivuje jednu událost značek a poté se zastaví.

4.  Pokud chcete zobrazit nové časovač v akci, přejděte do editoru kódu a přidejte následující kód v horní a dolní části `label_Click()` obslužná rutina události. (Přidáváte `if` příkaz na začátek a tři příkazy k dolnímu; zbytek metodu zůstává stejný.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kód v horní části metody kontroluje, zda časovač byl spuštěn kontrolou hodnotu **povoleno** vlastnost. Tímto způsobem, pokud přehrávač vybere první a druhý popisek ovládací prvky a spustí časovač, výběr třetí štítek, nebude to provádět žádné kroky.

     Kód v dolní části sady metoda `secondClicked` odkaz na proměnnou ke sledování, druhý ovládací prvek popisek přehrávač zvolili, a poté nastaví tento barvy ikony na černé vytvořit viditelné. Poté spustí časovač v jednorázovém režimu, takže čeká 750 milisekund a potom vyvolá jednu událost impulzu. Obslužná rutina události časovače značek skryje dvě ikony a obnoví `firstClicked` a `secondClicked` referenční proměnné, takže formuláře je připraven pro player zvolit jinou dvojici ikon.

5.  Uložte program a spusťte jej. Vyberte ikonu, která se stane viditelnou.

6.  Vyberte jinou ikonu. Objeví se krátce a pak obě ikony zmizí. Tento postup několikrát zopakujte. Formulář nyní sleduje první a druhou ikonu, které jste vybrali, a používá časovač k pozastavení před skrytím ikon.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 7: uchovejte páry viditelné](../ide/step-7-keep-pairs-visible.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 5: Přidejte odkazy na jmenovky](../ide/step-5-add-label-references.md).

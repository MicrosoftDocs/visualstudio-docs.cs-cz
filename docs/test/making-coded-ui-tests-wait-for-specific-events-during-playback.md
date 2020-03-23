---
title: Programové testy ui čekat na konkrétní události
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e594a6aec3f9e3a9664c5eac829b27f96f12ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584449"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Zajistěte, aby kódované testy ui čekaly na konkrétní události během přehrávání

V programovém přehrávání testu ui můžete dát pokyn, aby test počkal, až se objeví určité události, jako je například okno, indikátor průběhu zmizí a tak dále. Chcete-li to provést, použijte příslušnou metodu UITestControl.WaitForControlXXX(), jak je popsáno v následující tabulce. Příklad kódovaného testu ui, který čeká na povolení ovládacího prvku pomocí metody, naleznete v <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> [tématu Návod: Vytvoření, úpravy a údržba kódovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

Visual Studio Enterprise

> [!TIP]
> Můžete také přidat zpoždění před akcemi pomocí Editoru programových testů ui. Další informace naleznete v [tématu Postup: Vložení zpoždění před akcí ui pomocí Editoru testů programového rozhraní](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action).

**Metody UITestControl.WaitForControlXXX()**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Čeká na ovládací prvek, který má být připraven přijmout vstup myši a klávesnice. Modul implicitně volá toto rozhraní API pro všechny akce čekat na ovládací prvek připraven před provedením jakékoli operace. Však v některých esoterický scénář bude pravděpodobně muset provést explicitní volání.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Čeká na povolení ovládacího prvku, když průvodce provádí některé asynchronní ověření vstupu voláním na server. Můžete například čekat na povolení tlačítka **Další** průvodce (). Příklad této metody naleznete v [tématu Návod: Vytvoření, úpravy a údržba kódovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Čeká na ovládací prvek se zobrazí v ui. Například očekáváte chybový dialog poté, co aplikace provedla ověření parametrů. Doba pro ověření je variabilní. Tuto metodu můžete použít k čekání na chybové dialogové okno.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Čeká na ovládací prvek zmizí z ui. Můžete například počkat, až indikátor průběhu zmizí.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Čeká na zadanou vlastnost ovládacího prvku mít zadanou hodnotu. Například počkejte na text stavu změnit na **Hotovo**.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Čeká na zadanou vlastnost ovládacího prvku mít opak zadané hodnoty. Například počkejte, až nebude upravitelné pole jen pro čtení, tj.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Čeká na zadané predikátu vrátí `true`být . To lze použít pro komplexní operace čekání (například podmínky OR) na daném ovládacím prvku. Můžete například počkat, dokud nebude text stavu **úspěšný** nebo **neúspěšný,** jak je znázorněno v následujícím kódu:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);
```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

Všechny předchozí metody jsou instance metody UITestControl. Tato metoda je statickou metodou. Tato metoda také čeká na zadaný predikát být, `true` ale lze ji použít pro operaci komplexní čekání (jako podmínky OR) na více ovládacích prvků. Můžete například počkat, dokud nebude text stavu **úspěšný** nebo dokud se nezobrazí chybová zpráva, jak je znázorněno v následujícím kódu:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);
```

Všechny tyto metody mají následující chování:

Metody vrátí true, pokud čekání je úspěšné a false, pokud čekání se nezdařilo.

Implicitní časový režim pro operaci <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> čekání je určen vlastností. Výchozí hodnota této vlastnosti je 60000 milisekund (jedna minuta).

Metody mají přetížení, aby explicitní časový čas v milisekundách. Však pokud operace čekání má za následek implicitní hledání ovládacího prvku nebo, když je aplikace zaneprázdněna, skutečná čekací doba může být větší než časový rozsah zadaný.

Předchozí funkce jsou výkonné a flexibilní a měly by splňovat téměř všechny podmínky. Však v případě, že tyto metody nesplňují vaše <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>potřeby <xref:System.Threading.Thread.Sleep%2A> a je třeba kód buď , nebo v kódu, je doporučeno použít Playback.Wait() namísto Thread.Sleep() ROZHRANÍ API. Důvody jsou:

<xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>Vlastnost můžete použít k úpravě doby spánku. Ve výchozím nastavení je tato proměnná 1, ale můžete ji zvýšit nebo snížit a změnit čekací dobu v celém kódu. Například pokud testujete konkrétně přes pomalé sítě nebo jiné pomalé výkonu případu, můžete změnit tuto proměnnou na jednom místě (nebo dokonce v konfiguračním souboru) na 1,5 přidat 50 % další čekání na všech místech.

Playback.Wait() interně volá Thread.Sleep() (po výše uvedeném výpočtu) v menších blocích ve smyčce pro kontrolu operace zrušení\přerušení uživatele. Jinými slovy Playback.Wait() umožňuje zrušit přehrávání před koncem čekání vzhledem k tomu, že režim spánku nemusí nebo vyvolat výjimku.

> [!TIP]
> Programový editor testů ui umožňuje snadno upravit kódované testy ui. Pomocí Editoru testovaného rozhraní coded můžete vyhledat, zobrazit a upravit testovací metody. Akce ui a jejich přidružené ovládací prvky můžete také upravit v mapě ovládacího prvku ui. Další informace naleznete [v tématu Úprava kódovaných testů ui pomocí Editoru testů programového rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Návod: Vytvoření, úpravy a údržba kódovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomie kódovaného testu ui](../test/anatomy-of-a-coded-ui-test.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Postup: Vložení zpoždění před akcí ui pomocí programového editoru testů rozhraní](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)

---
title: Kódované testy výkonu webu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4297f60c74e32b904d7c36912a8377d33f23ebdf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589575"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generování a spuštění programového testu výkonnosti webu

Testy výkonu webu se zaznamenávají procházením webové aplikace. Testy jsou zahrnuty v zátěžových testech pro měření výkonu webové aplikace pod tlakem více uživatelů. Test výkonu webu lze převést na skript založený na kódu, který můžete upravit a přizpůsobit jako jakýkoli jiný zdrojový kód. Můžete například přidat smyčky a větvení konstrukce.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generovat kódovaný test výkonu webu

1. Pokud jste nevytvořili test výkonu webu, přečtěte si informace [o záznamu testu výkonu webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Vygenerujte kódovaný test.

     ![Generovat kódovaný test výkonu webu](../test/media/web_test_coded_generate.png)

3. Pojmenujte test.

     ![Zadejte název kódovaného testu výkonu webu.](../test/media/web_test_coded_generate_nametest.png)

     Nový kódovaný test se otevře v editoru kódu.

     V závislosti na tom, který výkon webu a šablona projektu zátěžového testu, kterou jste přidali do vašeho řešení, bude kód vygenerován v jazyce Visual Basic nebo Visual C#.

     ![V editoru kódu se otevře nový kódovaný test](../test/media/web_test_coded_generate_opencodeeditor.png)

     Můžete vidět v kódu, který GetRequestEnumerator() metoda v jazyce C#, nebo Run() metoda v jazyce Visual Basic, obsahuje každé ověřovací pravidlo a webový požadavek, který byl v překódovaný test.

4. Chcete-li demonstrovat přidání nějakého jednoduchého kódu, přejděte dolů na konec metody a za kód pro poslední webový požadavek a přidejte následující kód:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Vytvořte řešení a ověřte, zda se váš vlastní kód zkompiluje.

6. Spusťte test.

     ![Spuštění kódovaného testu výkonu webu](../test/media/web_test_coded_generate_run.png)

     A protože ten den, kdy se to rozběhla, byla středa...

     ![Výsledky testů výkonnosti webu](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Q&A

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Otázka: Mohu spustit více než jeden test najednou?
**A:** Ano, použijte v **Průzkumníku řešení**nabídku pravým tlačítkem myši (kontext).

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Otázka: Mám přidat zdroj dat před nebo po vygenerování kódovaného testu?
**A:** Je snazší přidat [zdroj dat](../test/add-a-data-source-to-a-web-performance-test.md) před generováním kódovaného testu, protože kód bude automaticky generován za vás.

Při spuštění kódovaného testu se zdrojem dat se může zobrazit následující chybová zpráva:

**Nelze spustit \<test Name> \<na název počítače agenta>: Odkaz na objekt není nastaven na instanci objektu.**

K tomu může dojít, protože máte DataSourceAttribute definované pro testovací třídu, bez odpovídající DataBindingAttribute. Chcete-li tuto chybu vyřešit, přidejte příslušný atribut DataBindingAttribute, odstraňte jej nebo zakomentujte z kódu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Otázka: Mám přidat ověřovací a extrakční pravidla před nebo po generování kódovaného testu?
**A:** Je snazší přidat ověřovací pravidla a pravidla extrakce před generováním kódovaného testu; doporučujeme však použít [kódované testy ui](../test/use-ui-automation-to-test-your-code.md) pro účely ověření.

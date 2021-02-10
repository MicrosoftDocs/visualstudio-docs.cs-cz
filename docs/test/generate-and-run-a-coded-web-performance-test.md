---
title: Kódované testy výkonnosti webu
description: Zjistěte, jak lze test výkonnosti webu převést na skript založený na kódu, který lze upravit a přizpůsobit.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 74269872992935568362a061d47f7335dbaedec8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936415"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generování a spuštění programového testu výkonnosti webu

Testy výkonnosti webu se zaznamenávají procházením vaší webové aplikace. Testy jsou obsaženy v zátěžových testech pro měření výkonu webové aplikace v rámci zátěže více uživatelů. Test výkonnosti webu lze převést na skript založený na kódu, který lze upravit a přizpůsobit stejným způsobem jako jakýkoli jiný zdrojový kód. Například můžete přidat konstrukce smyček a větvení.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generování kódovaného testu výkonnosti webu

1. Pokud jste nevytvořili test výkonnosti webu, přečtěte si téma [zaznamenat test výkonnosti webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Vygenerujte kódovaný test.

     ![Generování kódovaného testu výkonnosti webu](../test/media/web_test_coded_generate.png)

3. Pojmenujte test.

     ![Zadejte název kódovaného testu výkonnosti webu.](../test/media/web_test_coded_generate_nametest.png)

     Nový kódovaný test se otevře v editoru kódu.

     V závislosti na tom, který projekt webového výkonu a zátěžového testu, který jste přidali do řešení, se kód vygeneruje buď Visual Basic, nebo v jazyce Visual C#.

     ![V editoru kódu se otevře nový kódovaný test.](../test/media/web_test_coded_generate_opencodeeditor.png)

     Můžete vidět v kódu, který metoda GetRequestEnumerator () v jazyce C# nebo metoda Run () v Visual Basic obsahuje každé ověřovací pravidlo a webový požadavek, který byl v rámci převedený test.

4. Chcete-li předvést přidání jednoduchého kódu, přejděte dolů na konec metody a za kód poslední webové žádosti a přidejte následující kód:

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

5. Sestavte řešení, abyste ověřili, že váš vlastní kód kompiluje.

6. Spusťte test.

     ![Spuštění kódovaného testu výkonnosti webu](../test/media/web_test_coded_generate_run.png)

     A protože den, ke kterému došlo, se stal středu...

     ![Programové výsledky testu výkonnosti webu](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Otázky a odpovědi

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Otázka: mohu spustit více než jeden test současně?
**A:** Ano, můžete použít místní nabídku (kontext) na **Průzkumník řešení**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Otázka: mám přidat zdroj dat před nebo po vygenerování kódovaného testu?
**A:** Před vygenerováním kódovaného testu je snazší přidat [zdroj dat](../test/add-a-data-source-to-a-web-performance-test.md) , protože kód bude automaticky vygenerován za vás.

Při spuštění kódovaného testu se zdrojem dat se může zobrazit následující chybová zpráva:

**Nelze spustit test \<Test Name> na agentovi \<Computer Name> : odkaz na objekt není nastaven na instanci objektu.**

K tomu může dojít, protože máte definovanou DataSourceAttribute pro třídu testu bez odpovídajícího DataBindingAttribute. Chcete-li tuto chybu vyřešit, přidejte odpovídající DataBindingAttribute, odstraňte ji nebo přidejte komentář z kódu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Otázka: mám přidat pravidla ověřování a extrakce před nebo po vygenerování kódovaného testu?
**A:** Před vygenerováním kódovaného testu je snazší přidat pravidla ověřování a pravidla pro extrakci. Nicméně doporučujeme, abyste pro účely ověřování používali programové [testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md) .

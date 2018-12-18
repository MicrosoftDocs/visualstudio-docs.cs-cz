---
title: Kódované testy webového výkonu
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8a4e1ea45b8fe3ae0e33064973fcf1bc3517598e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067839"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generování a spuštění programového testu výkonnosti webu

Testy webového výkonu jsou zaznamenány procházením webové aplikace. Testy jsou zahrnuty v zátěžových testech k měření výkonu webové aplikace v rámci zátěže více uživatelů. Test výkonnosti webu lze převést na skript založený na kódu, který můžete upravit a přizpůsobit stejně jako jiný zdrojový kód. Můžete například přidat konstrukce větvení a smyček.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generování programový test výkonnosti webu

1.  Pokud jste ještě nevytvořili test výkonnosti webu, přečtěte si téma [zaznamenání testu výkonu webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project?view=vsts).

2.  Generovat kódovaný test.

     ![Generování programový test výkonnosti webu](../test/media/web_test_coded_generate.png)

3.  Název testu.

     ![Zadejte název programového testu výkonnosti webu](../test/media/web_test_coded_generate_nametest.png)

     V editoru kódu se otevře nový kódovaný test.

     V závislosti na tom, které webového výkonu a zatížení testovací projekt šablony jste přidali do svého řešení se vygeneruje kód v jazyce Visual Basic nebo Visual C#.

     ![V editoru kódu se otevře nový kódovaný test](../test/media/web_test_coded_generate_opencodeeditor.png)

     Zobrazí se v kódu, že metoda GetRequestEnumerator() v C# nebo metoda Run() v jazyce Visual Basic obsahuje každý ověřovací pravidlo a webové požadavky, které byly v zaznamenaném testu.

4.  Pokud chcete prokázat Přidání jednoduchého kódu, přejděte na konec metody a za kód poslední webové žádosti a přidejte následující kód:

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

5.  Sestavte řešení, chcete-li ověřit, že váš vlastní kód zkompiluje.

6.  Spusťte test.

     ![Spustit programový test výkonnosti webu](../test/media/web_test_coded_generate_run.png)

     A protože den toto bylo spuštěno právě ve středu...

     ![Výsledky testu webového výkonu](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>FUNKCE Q &AMP; A

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Dotaz: lze současně spustit více než jeden test?
 **Odpověď:** Ano, pomocí místní nabídky v **Průzkumníka řešení**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Dotaz: je třeba přidat zdroj dat, před nebo po generování kódovaného testu?
 **O:** je snadno přidávat [zdroj dat](../test/add-a-data-source-to-a-web-performance-test.md) před generováním kódovaného testu, protože kód se automaticky vygeneruje pro vás.

 Když spustíte programový test se zdrojem dat, může se zobrazit následující chybová zpráva:

 **Nelze spustit test \<název testu > na agentovi \<název počítače >: není nastavený na instanci objektu odkaz na objekt.**

 Tato situace může nastat, protože máte definovaný atribut pro třídu testování bez odpovídajícího atributu databindingattribute Datasourceattribute. Chcete-li vyřešit tuto chybu, přidejte odpovídající DataBindingAttribute, odstraňte ho nebo komentář z kódu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Dotaz: je třeba přidání pravidel ověřování a extrakce, před nebo po generování kódovaného testu?
 **Odpověď:** je snazší pro přidání pravidel ověřování a pravidla extrakce před generováním kódovaného testu; doporučujeme však, že používáte [programové testy UI](../test/use-ui-automation-to-test-your-code.md) pro účely ověření.
---
title: Rozhraní API zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ea28bba2d59515ce8080d577248dd7bddee0c570
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049902"
---
# <a name="how-to-use-the-load-test-api"></a>Postupy: použití rozhraní API zátěžového testu

Visual Studio podporuje zátěžového testu moduly plug-in kterých můžete ovládací prvek nebo vylepšit zátěžového testu. Test zatížení moduly plug-in jsou uživatelem definované třídy, které implementují <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> součástí rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů. Zátěžového testu pro moduly plug-in povolit ovládacího prvku vlastní zátěžového testu, jako jsou například přerušování zátěžového testu při splnění prahové hodnoty čítače nebo chyba. Pomocí vlastností na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> definována třída získat nebo nastavit parametry testu zatížení z uživatelského kódu. Použití událostí na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> třídy připojit delegáty pro oznámení, když je spuštěn zátěžový test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ke kontrole použijte prohlížeč objektů <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů. Editory Visual C# i Visual Basic nabízí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro testy výkonnosti webu. Další informace najdete v tématu [postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md) a [postupy: vytvoření modulu Plugin úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Používání oboru názvů LoadTesting

1.  Otevřete webový výkon a projekt zátěžového testu, který obsahuje zátěžový test.

2.  Přidejte Visual C# nebo Visual Basic projekt knihovny tříd pro vaše řešení pro testování.

3.  Přidáte odkaz v projektu webového výkonu a zátěžový test do projektu knihovny tříd.

4.  V projektu knihovny tříd přidejte odkaz na knihovnu DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework.

5.  Soubor třídy nachází v projektu knihovny tříd, přidejte `using` příkaz pro <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů.

6.  Vytvořte veřejnou třídu, která implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> rozhraní.

7.  Sestavte projekt.

8.  Přidáte nový zátěžový test modulu plug-in pomocí editoru zátěžových testů:

    1.  Klikněte pravým tlačítkem na kořenový uzel zátěžového testu a pak zvolte **přidat modul Plug-in zátěžového testu**.

    2.  **Přidat modul Plug-in zátěžového testu** se zobrazí dialogové okno.

    3.  V **vlastnosti pro vybraný modul plug-in** podokno, nastavte počáteční hodnoty pro modul plug-in pro použití v době běhu.

        > [!NOTE]
        > Lze vystavit libovolný počet vlastností chcete z modulů plug-in. Je třeba je nastavit veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in zátěžového testu můžete také upravit později pomocí **vlastnosti** okna.

9. Spuštění zátěžového testu.

     Implementace <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, naleznete v tématu [postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: použití API testu výkonnosti webu](../test/how-to-use-the-web-performance-test-api.md)
- [Postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md)
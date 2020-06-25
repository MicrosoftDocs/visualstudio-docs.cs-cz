---
title: Testování rozsáhlé aplikace s více mapami uživatelského rozhraní
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99e703d10d2bc6ed8fd573f4973e73f7ad40a937
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286580"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testování rozsáhlé aplikace s více mapami uživatelského rozhraní

Toto téma popisuje, jak používat kódované testy uživatelského rozhraní při testování rozsáhlých aplikací pomocí více mapování uživatelského rozhraní.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

Při vytváření nového programového testu uživatelského rozhraní generuje testovací architektura sady Visual Studio ve výchozím nastavení ve třídě [UIMap](/previous-versions/dd580454(v=vs.140)) kód pro test. Další informace o tom, jak zaznamenat programové testy UI, najdete v tématu Vytvoření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md) a [anatomie programového testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md).

Generovaný kód pro mapu uživatelského rozhraní obsahuje třídu pro každý objekt, se kterým pracuje test. Pro každou vygenerovanou metodu je doprovodná třída pro parametry metody generována speciálně pro tuto metodu. Pokud je ve vaší aplikaci velký počet objektů, stránek a formulářů a ovládacích prvků, mapa uživatelského rozhraní se může zvětšovat velmi veliké. Pokud na testech pracuje více lidí, aplikace se bude nepraktický s jedním velkým souborem mapování uživatelského rozhraní.

Používání více souborů mapa uživatelského rozhraní může mít následující výhody:

- Každá mapa může být přidružena k logické podmnožině aplikace. To usnadňuje správu změn.

- Každý tester může pracovat na oddílu aplikace a vrátit se změnami kód bez rušivého vlivu na jiné testery aplikace.

- Doplňování uživatelského rozhraní aplikace lze škálovat přírůstkově s minimálním dopadem na testy pro jiné části uživatelského rozhraní.

## <a name="do-you-need-multiple-ui-maps"></a>Potřebujete několik mapování uživatelského rozhraní?
Vytvoření více mapování uživatelského rozhraní v každém z těchto typů situací:

- Několik komplexních sad složených ovládacích prvků uživatelského rozhraní, které společně provádějí logickou operaci, například registrační stránku na webu nebo na stránce nákup nákupního košíku.

- Nezávislá sada ovládacích prvků, která je k dispozici z různých bodů aplikace, jako je například Průvodce s několika stránkami operací. Pokud je každá stránka průvodce zvlášť složitá, můžete pro každou stránku vytvořit samostatná mapování uživatelského rozhraní.

## <a name="add-multiple-ui-maps"></a>Přidání více mapování uživatelského rozhraní

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Chcete-li přidat mapu uživatelského rozhraní do projektu programového testu uživatelského rozhraní

1. V **Průzkumník řešení**vytvořte složku v projektu programového testu uživatelského rozhraní pro uložení všech map uživatelského rozhraní, klikněte pravým tlačítkem na soubor projektu programového testu UI, přejděte na **Přidat**a pak zvolte **Nová složka**. Můžete ho například pojmenovat `UIMaps` .

    Nová složka se zobrazí v rámci projektu programového testu uživatelského rozhraní.

2. Klikněte pravým tlačítkem na `UIMaps` složku, přejděte na **Přidat**a pak zvolte **Nová položka**.

    Zobrazí se dialogové okno **Přidat novou položku**.

   > [!NOTE]
   > Chcete-li přidat novou mapu programového testu UI, musíte být v projektu programového testu uživatelského rozhraní.

3. Ze seznamu vyberte mapa programového **testu uživatelského rozhraní** .

    Do pole **název** zadejte název nového mapování uživatelského rozhraní. Použijte název součásti nebo stránky, kterou bude mapa představovat, například `HomePageMap` .

4. Klikněte na tlačítko **Přidat**.

    Okno sady Visual Studio se minimalizuje a zobrazí se dialogové okno Tvůrce programového **testu uživatelského rozhraní** .

5. Zaznamenejte akce pro první metodu a vyberte možnost **generovat kód**.

6. Po zaznamenání všech akcí a kontrolních výrazů pro první komponentu nebo stránku a jejich seskupení do metod zavřete dialogové okno Tvůrce programového **testu uživatelského rozhraní** .

7. Pokračujte v vytváření map uživatelského rozhraní. Zaznamenejte akce a kontrolní výrazy, seskupte je do metod pro každou komponentu a potom kód vygenerujte.

   V mnoha případech zůstane okno aplikace na nejvyšší úrovni pro všechny průvodce, formuláře a stránky konstantní. Přestože má každá mapa uživatelského rozhraní třídu pro okno nejvyšší úrovně, všechny mapy se pravděpodobně odkazují na stejné okno nejvyšší úrovně, ve kterém se spustí všechny komponenty aplikace. Programové testy uživatelského rozhraní hledají ovládací prvky hierarchicky shora dolů, počínaje z okna nejvyšší úrovně, takže ve složitých aplikacích může být reálné okno nejvyšší úrovně duplicitní v každé mapě uživatelského rozhraní. Pokud je reálné okno nejvyšší úrovně duplicitní, bude při změně tohoto okna provedeny několik úprav. To může způsobit problémy s výkonem při přepínání mezi mapami uživatelského rozhraní.

   K minimalizaci tohoto efektu můžete použít `CopyFrom()` metodu k zajištění toho, aby nové okno nejvyšší úrovně v této mapě uživatelského rozhraní bylo stejné jako v hlavním okně nejvyšší úrovně.

## <a name="example"></a>Příklad

Následující příklad je součástí třídy nástrojů, která poskytuje přístup k jednotlivým komponentám a jejich podřízeným ovládacím prvkům, které jsou reprezentovány třídami generovanými v různých mapách uživatelského rozhraní.

V tomto příkladu má webová aplikace s názvem stránku `Contoso` domů, stránku produktu a nákupní košík. Každá z těchto stránek sdílí společné okno nejvyšší úrovně, což je okno prohlížeče. K dispozici je mapa uživatelského rozhraní pro každou stránku a třída utility má kód podobný následujícímu:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytvořit kódované testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Anatomie kódovaného testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md)

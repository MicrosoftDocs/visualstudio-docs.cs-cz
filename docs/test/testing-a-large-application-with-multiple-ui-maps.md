---
title: Testování rozsáhlé aplikace s více mapami uživatelského rozhraní
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fa5afd01ad25d4eebdc0b29e924cb2430d9c775
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590290"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testování velké aplikace s více mapami ui

Toto téma popisuje, jak používat kódované testy ui při testování velké aplikace pomocí více map ui.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

Při vytváření nového test umítaného rozhraní, Visual Studio testování rozhraní generuje kód pro test ve výchozím nastavení ve třídě [UIMap.](/previous-versions/dd580454(v=vs.140)) Další informace o tom, jak zaznamenat kódované testy ui, naleznete [v tématu Vytvoření kódovaných testů rozhraní](../test/use-ui-automation-to-test-your-code.md) a [anatomie programového testu ui](../test/anatomy-of-a-coded-ui-test.md).

Generovaný kód pro mapu ui obsahuje třídu pro každý objekt, se kterým test spolupracuje. Pro každou vygenerovanou metodu je generována doprovodná třída pro parametry metody speciálně pro tuto metodu. Pokud existuje velký počet objektů, stránek a formulářů a ovládacích prvků ve vaší aplikaci, mapa ui může zvětšit velmi velké. Také pokud několik lidí pracuje na testech, aplikace se stane nepraktický s jedním velkým souborem mapy ui.

Použití více souborů mapy ui může poskytnout následující výhody:

- Každá mapa může být přidružena k logické podmnožině aplikace. To usnadňuje správu změn.

- Každý tester může pracovat na části aplikace a zkontrolovat jejich kód bez zásahu s ostatními testery pracujícími na jiných částech aplikace.

- Přírůstky do ui aplikace lze škálovat postupně s minimálním dopadem na testy pro jiné části rozhraní.

## <a name="do-you-need-multiple-ui-maps"></a>Potřebujete více map ui?
Vytvořte více map ui v každém z těchto typů situací:

- Několik složitých sad složených ovládacích prvků rozhraní, které společně provádějí logickou operaci, například registrační stránku na webu nebo nákupní stránku nákupního košíku.

- Nezávislá sada ovládacích prvků, která je přístupná z různých bodů aplikace, jako je například průvodce s několika stránkami operací. Pokud je každá stránka průvodce obzvláště složitá, můžete pro každou stránku vytvořit samostatné mapy ui.

## <a name="add-multiple-ui-maps"></a>Přidání více map ui

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Přidání mapy ui do programového testovacího projektu ui

1. Chcete-li v **Průzkumníkovi řešení**vytvořit složku v programovém testovacím projektu ui pro uložení všech map ui, klepněte pravým tlačítkem myši na kódovaný soubor testovacího projektu rozhraní, přejděte na **Přidat**a pak zvolte **Nová složka**. Můžete jej například `UIMaps`pojmenovat .

    Nová složka se zobrazí pod programovým testovacím projektem ui.

2. Klikněte pravým `UIMaps` tlačítkem myši na složku, přejděte na **Přidat**a pak zvolte **Nová položka**.

    Zobrazí se dialogové okno **Přidat novou položku**.

   > [!NOTE]
   > Chcete-li přidat novou kódovnou testovací mapu rozhraní, musíte být v programovém testovacím projektu ui.

3. V seznamu vyberte **Kódované mapování testů ui.**

    Do pole **Název** zadejte název nové mapy uživatelského rozhraní. Použijte název komponenty nebo stránky, kterou bude mapa `HomePageMap`představovat, například .

4. Zvolte **Přidat**.

    Okno Sady Visual Studio se minimalizuje a zobrazí se dialogové okno **Tvůrce testů usměrněného ui.**

5. Zaznamenejte akce pro první metodu a zvolte **Generovat kód**.

6. Po zaznamenání všech akcí a kontrolních výrazů pro první komponentu nebo stránku a jejich seskupení do metod zavřete dialogové okno **Tvůrce testovaného ui.**

7. Pokračujte ve vytváření map ui. Zaznamenejte akce a kontrolní výrazy, seskupte je do metod pro každou komponentu a pak vygenerujte kód.

   V mnoha případech zůstává okno nejvyšší úrovně aplikace konstantní pro všechny průvodce, formuláře a stránky. Přestože každá mapa ui má třídu pro okno nejvyšší úrovně, všechny mapy pravděpodobně odkazují na stejné okno nejvyšší úrovně, ve kterém jsou spuštěny všechny součásti aplikace. Programové testy ui vyhledávají ovládací prvky hierarchicky shora dolů, počínaje oknem nejvyšší úrovně, takže ve složité aplikaci může být skutečné okno nejvyšší úrovně duplikováno v každé mapě ui. Pokud je okno skutečné nejvyšší úrovně duplikováno, dojde k několika úpravám, pokud se toto okno změní. To může způsobit problémy s výkonem při přepínání mezi mapami ui.

   Chcete-li tento efekt minimalizovat, můžete pomocí `CopyFrom()` metody zajistit, aby nové okno nejvyšší úrovně v této mapě ui je stejné jako hlavní okno nejvyšší úrovně.

## <a name="example"></a>Příklad

Následující příklad je součástí utility třídy, která poskytuje přístup ke každé součásti a jejich podřízené ovládací prvky, které jsou reprezentovány třídy generované v různých mapách ui.

V tomto příkladu má `Contoso` webová aplikace domovskou stránku, stránku produktu a stránku nákupního košíku. Každá z těchto stránek sdílí společné okno nejvyšší úrovně, což je okno prohlížeče. Pro každou stránku je mapa ui a třída nástroje má kód podobný následujícímu:

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
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Anatomie kódovaného testu ui](../test/anatomy-of-a-coded-ui-test.md)
